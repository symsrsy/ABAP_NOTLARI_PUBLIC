REPORT zmalzeme_detay_alv.

TABLES: mara.

TYPE-POOLS: slis.

" Kullanıcı girişi
PARAMETERS: p_matnr TYPE matnr OBLIGATORY.

" BAPI'den gelen yapı
DATA: ls_material_data TYPE bapimatdoa.

" ALV için kullanılacak yapı
TYPES: BEGIN OF ty_malzeme,
         matnr      TYPE matnr,
         matl_desc  TYPE bapimatdoa-matl_desc,
         matl_type  TYPE bapimatdoa-matl_type,
         base_uom   TYPE bapimatdoa-base_uom,
         created_on TYPE bapimatdoa-created_on,
         created_by TYPE bapimatdoa-created_by,
       END OF ty_malzeme.

DATA: gt_malzeme TYPE TABLE OF ty_malzeme,
      gs_malzeme TYPE ty_malzeme.

DATA: gt_fcat TYPE slis_t_fieldcat_alv,
      gs_fcat TYPE slis_fieldcat_alv.

START-OF-SELECTION.

  " BAPI ile veri çek
  CALL FUNCTION 'BAPI_MATERIAL_GET_DETAIL'
    EXPORTING
      material = p_matnr
    IMPORTING
      material_general_data = ls_material_data.

  " ALV için tabloya aktarma
  gs_malzeme-matnr      = p_matnr.
  gs_malzeme-matl_desc  = ls_material_data-matl_desc.
  gs_malzeme-matl_type  = ls_material_data-matl_type.
  gs_malzeme-base_uom   = ls_material_data-base_uom.
  gs_malzeme-created_on = ls_material_data-created_on.
  gs_malzeme-created_by = ls_material_data-created_by.
  APPEND gs_malzeme TO gt_malzeme.

  " ALV Fieldcatalog
  PERFORM build_fieldcat.

  " ALV Gösterimi
  CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
    EXPORTING
      it_fieldcat = gt_fcat
    TABLES
      t_outtab    = gt_malzeme.


FORM build_fieldcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'MATNR'.
  gs_fcat-coltext   = 'Malzeme No'.
  APPEND gs_fcat TO gt_fcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'MATL_DESC'.
  gs_fcat-coltext   = 'Malzeme Tanımı'.
  APPEND gs_fcat TO gt_fcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'MATL_TYPE'.
  gs_fcat-coltext   = 'Malzeme Türü'.
  APPEND gs_fcat TO gt_fcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'BASE_UOM'.
  gs_fcat-coltext   = 'Temel Ölçü Birimi'.
  APPEND gs_fcat TO gt_fcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'CREATED_ON'.
  gs_fcat-coltext   = 'Oluşturma Tarihi'.
  APPEND gs_fcat TO gt_fcat.

  CLEAR gs_fcat.
  gs_fcat-fieldname = 'CREATED_BY'.
  gs_fcat-coltext   = 'Oluşturan Kişi'.
  APPEND gs_fcat TO gt_fcat.

ENDFORM.

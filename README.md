@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'DAM - Dados Mestre/Item'
@Metadata.ignorePropagatedAnnotations: true
@ObjectModel.usageType:{
    serviceQuality: #X,
    sizeCategory: #S,
    dataClass: #MIXED
}
 
define view entity /FHG2/R_TDAM_HDR_ITM
  as select from /fhg/tdam               as H
    association [1..*] to /fhg/tdam_item as I
      on $projection.Damid = I.damid  
  
    //inner join   /fhg/tdam_item as I on H.damid = I.damid
{
  key H.damid as Damid,
  key I.damit as Damit,
 
      H.txjcd             as TaxJurCode,
      H.oriid             as OriId,
      H.oriit             as OriIt,
      H.tprec             as Tprec,
      H.begda             as Begda,
      H.endda             as Endda,
      H.budat             as Budat,
      H.dt_recolh         as DtRecolh,
      H.cancel            as Cancel,
      H.candat            as CanDat,
      H.bukrs             as Bukrs,
      H.branch            as Branch,
      H.fornecedor        as Fornecedor,
      H.vencimento        as Vencimento,
      H.tp_lancto         as TpLancto,
      H.referencia        as Referencia,
      H.cod_proc          as CodProc,
      H.emitente          as Emitente,
      H.emissao           as Emissao,
      H.receber_ate       as ReceberAte,
      H.waers             as Currency,
      @Semantics.amount.currencyCode: 'Currency'
      H.vlr_total         as VlrTotal,
      @Semantics.amount.currencyCode: 'Currency'
      H.vlr_ja_pago      as VlrJaPago,
      @Semantics.amount.currencyCode: 'Currency'
      H.vlr_multa        as VlrMulta,
      @Semantics.amount.currencyCode: 'Currency'
      H.vlr_juros        as VlrJuros,
      @Semantics.amount.currencyCode: 'Currency'
      H.vlr_outras       as VlrOutras,
      @Semantics.amount.currencyCode: 'Currency'
      H.cormon           as CormonHdr,
      @Semantics.amount.currencyCode: 'Currency'
      H.incentivo        as Incentivo,
      //@Semantics.amount.currencyCode: 'Currency'
      H.waers            as Waers,
      @Semantics.amount.currencyCode: 'Currency'
      H.tax_emol         as TaxEmol,
      H.pgtid            as PgtId,
      
      H.setid            as SetId,
      H.imp_guia         as ImpGuia,
      H.debid            as DebId,
      H.extra_key        as ExtraKey,
      H.crenam           as CreNam,
      H.credat           as CreDat,
      H.cretim           as CreTim,
 
      I.oritp            as OriTp,
      @Semantics.amount.currencyCode : 'waers'
      I.receita          as Receita,
      @Semantics.amount.currencyCode : 'waers'
      I.deducao          as Deducao,
      I.aliquota         as Aliquota,
      @Semantics.amount.currencyCode : 'waers'
      I.vlrorig          as VlrOrig,
      @Semantics.amount.currencyCode : 'waers'
      I.juros            as JurosItm,
      @Semantics.amount.currencyCode : 'waers'
      I.cormon           as CormonItm,
      @Semantics.amount.currencyCode : 'waers'
      I.multa            as MultaItm,
      @Semantics.amount.currencyCode : 'waers'
      I.valor            as Valor,
      @Semantics.amount.currencyCode : 'waers'
      I.tax_emol         as TaxEmolItm
}

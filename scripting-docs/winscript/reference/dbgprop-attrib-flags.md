---
title: "DBGPROP_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_ATTRIB_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DBGPROP_ATTRIB_FLAGS
Décrit plusieurs attributs d'un objet `IDebugProperty`.  Membre de la structure `DebugPropertyInfo`.  
  
## Syntaxe  
  
```  
enum { DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,    DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,    DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,    DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,    DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,    DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,    DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,    DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,    DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,    DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,    DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,    DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,    DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,    DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,    DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,    DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000    DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000, };   
```  
  
## Membres  
 DBGPROP\_ATTRIB\_NO\_ATTRIB  
 Indique l'absence d'attribut.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_INVALID  
 Indique que la valeur de `DebugPropertyInfo::bstrValue` n'est pas valide.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_EXPANDABLE  
 Indique que la référence ou la propriété a des enfants.  
  
 DBGPROP\_ATTRIB\_VALUE\_READONLY  
 Indique que la valeur est en lecture seule.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PUBLIC  
 Indique un objet qui possède un accès public.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PRIVATE  
 Indique un objet qui possède un accès privé.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PROTECTED  
 Indique un objet qui possède un accès protégé.  
  
 DBGPROP\_ATTRIB\_ACCESS\_FINAL  
 Indique un objet qui possède un accès final.  
  
 DBGPROP\_ATTRIB\_STORAGE\_GLOBAL  
 Indique un stockage global.  
  
 DBGPROP\_ATTRIB\_STORAGE\_STATIC  
 Indique un stockage statique.  
  
 DBGPROP\_ATTRIB\_STORAGE\_FIELD  
 Indique un objet qui est une propriété.  
  
 DBGPROP\_ATTRIB\_STORAGE\_VIRTUAL  
 Indique un stockage virtuel.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_CONSTANT  
 Indique que le type d'objet est constant.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_SYNCHRONIZED  
 Indique que cet emplacement est synchronisé par thread.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_VOLATILE  
 Indique que cet emplacement est volatile par rapport à un stockage persistant.  
  
 DBGPROP\_ATTRIB\_HAS\_EXTENDED\_ATTRIBS  
 Indique que cet emplacement a des attributs au\-dessus et au\-delà de ces bits prédéfinis.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_RETURN\_VALUE  
 Indique que la valeur est une valeur de retour d'une fonction.  
  
## Notes  
 Ces indicateurs sont également utilisés pour filtrer les enfants d'un objet.  Les valeurs peuvent être combinées avec une opération OR au niveau du bit.  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo, structure](../../winscript/reference/debugpropertyinfo-structure.md)
---
title: "&#201;num&#233;rateur de Code de statut de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "constantes nommées, SccStatus énumérateur"
  - "contrôle plug-ins de source, énumération l'état de fichier"
  - "Énumérateur de SccStatus"
  - "énumérateur de code de statut de fichier"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# &#201;num&#233;rateur de Code de statut de fichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le `SccStatus` énumérateur contient des valeurs de constantes nommées qui spécifient l'état d'un fichier dans le système de contrôle de code source. Cette énumération est utilisée par le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et le `POPLISTFUNC` fonction de rappel \(voir [POPLISTFUNC](../extensibility/poplistfunc.md) Pour plus d'informations\).  
  
## Syntaxe  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## Membres  
 SCC\_STATUS\_INVALID  
 État n'a pas pu être obtenu ; ne comptez pas sur ce dernier.  
  
 SCC\_STATUS\_NOTCONTROLLED  
 Fichier n'est pas sous contrôle de code source.  
  
 SCC\_STATUS\_CONTROLLED  
 Fichier est sous contrôle de code source.  
  
 SCC\_STATUS\_CHECKEDOUT  
 Extrait par l'utilisateur actuel sur le disque local.  
  
 SCC\_STATUS\_OUTOTHER  
 Fichier est extrait par un autre utilisateur.  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 Fichier est extrait en mode exclusif.  
  
 SCC\_STATUS\_OUTMULTIPLE  
 Fichier est extrait par plusieurs utilisateurs.  
  
 SCC\_STATUS\_OUTOFDATE  
 Le fichier n'est pas la plus récente.  
  
 SCC\_STATUS\_DELETED  
 Fichier a été supprimé du projet.  
  
 SCC\_STATUS\_LOCKED  
 Fichier est verrouillé ; pas de versions plus autorisées.  
  
 SCC\_STATUS\_MERGED  
 Fichier a été fusionné mais pas encore fixe\/vérifié.  
  
 SCC\_STATUS\_SHARED  
 Fichier est partagé entre les projets.  
  
 SCC\_STATUS\_PINNED  
 Fichier est partagé à une version explicite.  
  
 SCC\_STATUS\_MODIFIED  
 Fichier a été modifié, divisé\/violée.  
  
 SCC\_STATUS\_OUTBYUSER  
 Fichier est extrait par l'utilisateur actuel.  
  
 SCC\_STATUS\_NOMERGE  
 Fichier ne peut jamais être fusionnée avec et ne doit pas être enregistré avant une opération GET.  
  
 SCC\_STATUS\_RESERVED\_1  
 Réservé à un usage interne.  
  
 SCC\_STATUS\_RESERVED\_2  
 Réservé à un usage interne.  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
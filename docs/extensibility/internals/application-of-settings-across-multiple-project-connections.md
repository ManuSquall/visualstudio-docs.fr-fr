---
title: "Application des param&#232;tres entre plusieurs connexions de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, l'application des paramètres"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Application des param&#232;tres entre plusieurs connexions de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un plug\-in contrôle de code source généré à l'aide de l'API des plug\-ins 1,2 de contrôle de code source, peut utiliser un traitement par lots pour effectuer la même opération de contrôle de code source dans plusieurs projets ou plusieurs contextes de connexion.  Lots peuvent être utilisés pour éliminer redondant, boîtes de dialogue de par projet de l'expérience utilisateur.  
  
 Si un utilisateur active plusieurs éléments qui appartiennent à plusieurs connexions dans un plug\-in contrôle de code source généré à l'aide de l'API des plug\-ins 1,1 de contrôle de code source, \(par exemple, deux projets Web sur des ordinateurs différents de partage de fichiers\) et les extraire, l'utilisateur voit identique à la boîte de dialogue à plusieurs reprises.  Cela se produit même si l'utilisateur clique sur la case à cocher d' **Appliquez à tous** dans la boîte de dialogue, car l'IDE réinitialise son état pour chaque contexte de connexion.  
  
## Balise de fonction  
 la fonction d'`SccBeginBatch` définit la balise d' `SCC_CAP_BATCH` pour indiquer qu'un traitement par lots est en cours  
  
## nouvelles fonctions  
 Les nouvelles fonctionnalités suivantes prennent en charge le traitement par lots :  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 La fonction d' `SCCBeginBatch` démarre un groupe d'opérations de contrôle de code source.  `SccEndBatch` ferme le groupe.  les groupes peuvent ne pas être imbriqués.  
  
## Voir aussi  
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
---
title: "Les param&#232;tres &#39;InterfaceId&#39; et &#39;EventsId&#39; pour &#39;Microsoft.VisualBasic.ComClassAttribute&#39; sur &#39;&lt;nom_type&gt;&#39; ne peuvent pas avoir la m&#234;me valeur | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres &#39;InterfaceId&#39; et &#39;EventsId&#39; pour &#39;Microsoft.VisualBasic.ComClassAttribute&#39; sur &#39;&lt;nom_type&gt;&#39; ne peuvent pas avoir la m&#234;me valeur
Un bloc d’attributs `COMClassAttribute` spécifie le même identificateur global unique \(GUID\) pour l’interface et pour l’événement de création. Si vous fournissez ces deux identificateurs, ils doivent être différents. Ils doivent également être différents de l’identificateur de classe.  
  
 Un GUID se compose de 16 octets, dont les huit premiers sont numériques et les huit derniers sont binaires. Il est généré par des utilitaires Microsoft tels que uuidgen.exe et son caractère unique est garanti.  
  
 **ID d’erreur :** BC32507  
  
### Pour corriger cette erreur  
  
1.  Déterminez les GUID corrects nécessaires pour identifier l’interface et l’événement de création de l’objet COM.  
  
2.  Vérifiez que les chaînes de GUID présentées au bloc d’attributs `COMClassAttribute` sont copiées correctement.  
  
## Voir aussi  
 [NOT IN BUILD : attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute \(classe\)](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)
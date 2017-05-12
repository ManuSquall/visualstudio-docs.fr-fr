---
title: "D&#233;pannage de la s&#233;curit&#233; des solutions Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sécurité (développement Office dans Visual Studio), dépanner"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# D&#233;pannage de la s&#233;curit&#233; des solutions Office
  Cette rubrique contient des conseils pour résoudre des problèmes courants que vous pouvez rencontrer lorsque vous sécurisez des solutions Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Impossible d'installer des solutions approuvées à partir de sites sensibles  
 Les utilisateurs ne peuvent pas installer une solution à partir d'un emplacement Web si le site Web est répertorié dans la zone sites sensibles d'Internet Explorer.  Cela est vrai même si la solution est signée avec un certificat approuvé.  
  
 L'URL du manifeste de déploiement peut être catégorisée dans l'une des cinq zones :  
  
-   Poste de travail  
  
-   Internet  
  
-   Intranet local  
  
-   Sites de confiance  
  
-   Sites sensibles  
  
 Si l'emplacement du manifeste de déploiement a été assigné à la zone de sites sensibles, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] n'installe pas la solution.  Si l'emplacement est connu et fiable, l'utilisateur peut supprimer l'emplacement de la zone des sites sensibles et installer la solution.  Pour plus d'informations sur la gestion de zones, consultez [Configuration d'éditeurs approuvés ClickOnce \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Les solutions ne peuvent pas être installées à partir des partages de fichiers réseau ou des emplacements Web lorsque la configuration de la sécurité renforcée d'Internet Explorer ou d'Internet Explorer 7 est installée  
 La configuration de sécurité renforcée d'Internet Explorer \(IEESC\) dans Windows Server 2003 et version ultérieure, et Internet Explorer 7 et version ultérieure, restreint considérablement la capacité des utilisateurs de parcourir Internet.  Lorsque le test d'utilisateurs pour installer des solutions Office d'un emplacement de partage ou de Web de fichier réseau, elle peut recevoir le message d'erreur suivant : « La fonctionnalité personnalisée dans cette application ne fonctionnera pas car le certificat utilisé pour signer le manifeste de déploiement pour *SolutionName* n'est pas approuvé.  Contactez votre administrateur pour obtenir une aide supplémentaire. »  
  
 Avec IEESC et Internet Explorer 7 et version ultérieure, si l'URL du manifeste de déploiement est catégorisée dans la zone Internet, le manifeste doit avoir un certificat d'un éditeur approuvé ou la solution ne peut pas être installée.  Sans IEESC, le comportement par défaut consiste à inviter l'utilisateur final à prendre une décision d'approbation.  
  
 Pour gérer l'effet d'IEESC et Internet Explorer 7 et version ultérieure, identifiez les sites Web et les chemins de \(UNC\) de convention d'affectation de noms que vous y faites confiance et ajoutez l'une des zones de sécurité approuvées \(intranet local ou sites de confiance\). Pour plus d'informations sur la gestion des zones, consultez [Configurer des éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  
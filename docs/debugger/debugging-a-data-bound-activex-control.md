---
title: "D&#233;bogage d&#39;un contr&#244;le ActiveX li&#233; aux donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "contrôles ActiveX, débogage"
  - "contrôles (Visual Studio), ActiveX"
  - "contrôles liés aux données, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# D&#233;bogage d&#39;un contr&#244;le ActiveX li&#233; aux donn&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous développez un contrôle ActiveX qui sera lié à un contrôle de source de données, vous pouvez créer votre propre application conteneur et utiliser ce conteneur pour le débogage du contrôle ActiveX.  
  
 Par exemple, vous pouvez créer une application MFC basée sur des boîtes de dialogue et placer votre contrôle lié aux données et un contrôle de source de données dans la boîte de dialogue.  Vous pouvez utiliser cette application MFC pour le test d'exécution et comme exécutable conteneur pour déboguer votre contrôle ActiveX lié aux données.  
  
## Utilisation de Test Container  
 Si vous voulez qu'un conteneur facilement modifiable prenne en charge plusieurs interfaces sur le contrôle ou le conteneur, utilisez ActiveX Test Container comme exécutable pour la session de débogage.  Dans ActiveX Test Container, cliquez sur **Options** dans le menu **Conteneur** pour activer plusieurs interfaces.  Pour plus d'informations, consultez [Test des propriétés et des événements avec le conteneur de test](/visual-cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Si vous avez besoin d'effectuer un pas à pas détaillé dans le code du conteneur pendant le débogage, utilisez la version Debug de votre conteneur ou utilisez la version Debug d'ActiveX Test Container.  Pour plus d'informations, consultez [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/fr-fr/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Contrôles ActiveX](/visual-cpp/mfc/activex-controls)
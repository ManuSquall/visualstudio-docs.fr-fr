---
title: "Exemple de compl&#233;ment Excel pour le test cod&#233; de l&#39;interface utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tests codés de l'interface utilisateur, exemple de complément Excel"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Exemple de compl&#233;ment Excel pour le test cod&#233; de l&#39;interface utilisateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cet exemple de complément pour [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] est particulièrement conçu pour prendre en charge des tests codés de l'interface utilisateur de feuilles de calcul Excel qui sont enregistrés et exécutés dans Visual Studio Enterprise. Le complément est créé à l'aide de Visual Studio Tools pour Office.  
  
 Pour plus d'informations sur la création d'un complément Excel, consultez [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md) ou recherchez « Complément Excel » sur MSDN.  
  
 Bien que le complément Excel ne soit pas le sujet principal de cette documentation sur l'extension du test codé de l'interface utilisateur pour Excel, voici quelques commentaires utiles.  
  
 Parties importantes de ce complément :  
  
-   Classe `ThisAddIn` : gère le canal .NET Remoting entre le `ExcelUICommunicator` et l'[Exemple d’extension du test codé de l’interface utilisateur pour Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  : certificat de sécurité pour tester le complément.  
  
-   Classe `ExcelUICommunicator` : cette classe implémente l'interface `IExcelUICommunication`.  
  
## Classe ThisAddIn  
 La plupart de cette classe est en fait généré par Visual Studio Tools pour Office dans le fichier `ThisAddIn.Designer.cs` quand vous créez votre projet de complément Excel.  
  
 Les membres que vous devez implémenter sont les gestionnaires d'événements : `ThisAddIn_Startup()` et `ThisAddIn_Shutdown()`.  Leur but est d'initialiser ou de fermer le canal .NET Remoting utilisé par le `ExcelUICommunicator`.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Ce fichier contient un certificat de sécurité temporaire qui est généré par Visual Studio Tools pour Office et autorise l'assembly du complément à fonctionner dans le processus Excel pour tester le complément et l'extension.  Vous devez supprimer ce certificat et soit en créer un nouveau sous l'onglet **Signature** de la fenêtre **Propriétés** du projet, soit attacher votre propre certificat de test.  
  
## Classe ExcelUICommunicator  
 Cette classe implémente l'interface `IExcelUITestCommunication` et obtient les informations de l'interface utilisateur demandée à partir du modèle objet Excel.  Pour plus d'informations, voir [Exemple d'interface Communicator Excel](../test/sample-excel-communicator-interface.md)  
  
## Voir aussi  
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
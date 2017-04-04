---
title: "Exemple de complément Excel pour le test codé de l’interface utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 52b0394f0e52b8b7b640611253dcef693b4eca3c
ms.lasthandoff: 02/22/2017

---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Exemple de complément Excel pour le test codé de l'interface utilisateur
Cet exemple de complément pour [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] est particulièrement conçu pour prendre en charge des tests codés de l'interface utilisateur de feuilles de calcul Excel qui sont enregistrés et exécutés dans Visual Studio Enterprise. Le complément est créé à l’aide de Visual Studio Tools pour Office.  
  
 Pour plus d’informations sur la façon de créer un complément Excel, consultez [Procédure pas à pas : création de votre premier complément VSTO pour Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) ou recherchez « Complément Excel » sur MSDN.  
  
 Bien que le complément Excel ne soit pas le sujet principal de cette documentation sur l’extension du test codé de l’interface utilisateur pour Excel, voici quelques commentaires utiles.  
  
 Parties importantes de ce complément :  
  
-   Classe `ThisAddIn` : gère le canal .NET Remoting entre le `ExcelUICommunicator` et l’[exemple d’extension du test codé de l’interface utilisateur pour Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` : certificat de sécurité pour tester le complément.  
  
-   Classe `ExcelUICommunicator` : cette classe implémente l’interface `IExcelUICommunication`.  
  
## <a name="thisaddin-class"></a>Classe ThisAddIn  
 La plupart de cette classe est en fait généré par Visual Studio Tools pour Office dans le fichier `ThisAddIn.Designer.cs` quand vous créez votre projet de complément Excel.  
  
 Les membres que vous devez implémenter sont les gestionnaires d'événements : `ThisAddIn_Startup()` et `ThisAddIn_Shutdown()`. Leur but est d'initialiser ou de fermer le canal .NET Remoting utilisé par le `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Ce fichier contient un certificat de sécurité temporaire qui est généré par Visual Studio Tools pour Office et autorise l’assembly du complément à fonctionner dans le processus Excel pour tester le complément et l’extension. Vous devez supprimer ce certificat et soit en créer un nouveau sous l’onglet **Signature** de la fenêtre **Propriétés** du projet, soit attacher votre propre certificat de test.  
  
## <a name="exceluicommunicator-class"></a>Classe ExcelUICommunicator  
 Cette classe implémente l'interface `IExcelUITestCommunication` et obtient les informations de l'interface utilisateur demandée à partir du modèle objet Excel. Pour plus d’informations, consultez [Exemple d’interface Communicator Excel](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre en charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Procédure pas à pas : création de votre premier complément VSTO pour Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Développement Office et SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)


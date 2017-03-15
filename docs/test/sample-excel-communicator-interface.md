---
title: "Exemple d&#39;interface Communicator Excel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Exemple d&#39;interface Communicator Excel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'exemple d'interface `IExcelUICommunication` est utilisée dans l'objet `ExcelUICommunicator` du projet `ExcelAddIn`.  
  
## Interface IExcelUICommunication  
 Cette interface définit les points de communication entre le `CodedUIExtension`, qui s'exécute dans le processus des tests codés de l'interface utilisateur et l' `ExcelCodedUIAddIn`, qui s'exécute dans le processus [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 L'assembly `ExcelCodedUIAddinHelper` possède une classe `ExcelUICommunicator` dérivée de cette interface et utilise le modèle d'objet Excel pour traiter les méthodes.  
  
 Certaines méthodes récupèrent les informations dans Excel, puis créent et retournent l'un des objets d'informations, comme l'objet `CellInformation`.  
  
 D'autres méthodes utilisent un objet d'informations fourni, recherchent le contrôle correspondant dans Excel et exécutent des processus sur le contrôle.  Par exemple, la méthode `ScrollIntoView` fait défiler la feuille de calcul pour rendre la cellule désignée visible.  
  
## Communication CodedUIExtensibilitySample et ExcelCodedUIAddinHelper  
 L'assembly `ExcelCodedUIAddinHelper` s'exécute dans le processus Excel et possède la classe `UICommunicator` qui implémente l'interface `IExcelUITestCommunication` et obtient ou définit les informations nécessaires directement à partir de l'interface utilisateur Excel.  
  
 L'assembly `CodedUIExtensibilitySample` s'exécute dans le processus des tests codés de l'interface utilisateur de Visual Studio.  Cet assembly possède la classe `Communicator` qui ouvre un canal .NET Remoting et fournit une propriété `Instance` qui utilise l'interface `IExcelUICommunication` pour utiliser l'objet `UICommunicator` dans l'assembly `ExcelCodedUIAddinHelper` pour transmettre les requêtes et les objets d'informations, tels qu'un objet `CellInformation`, en se déplaçant entre les deux assemblys.  
  
## Voir aussi  
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Exemple de complément Excel pour le test codé de l'interface utilisateur](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Exemple d’extension du test codé de l’interface utilisateur pour Excel](../test/sample-coded-ui-test-extension-for-excel.md)
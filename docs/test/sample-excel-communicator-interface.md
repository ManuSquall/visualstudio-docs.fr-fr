---
title: "Exemple d’interface Communicator Excel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: aafc9ef6bd8f10e00b64a7bfb25fabc8fedb8b21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sample-excel-communicator-interface"></a>Exemple d'interface Communicator Excel
L’exemple d’interface `IExcelUICommunication` est utilisé dans l’objet `ExcelUICommunicator` du projet `ExcelAddIn`.  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication, interface  
 Cette interface définit les points de communication entre `CodedUIExtension`, qui s’exécute dans le processus de test codé de l’interface utilisateur et `ExcelCodedUIAddIn`, qui s’exécute dans le processus [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 L’assembly `ExcelCodedUIAddinHelper` a une classe`ExcelUICommunicator` qui dérive de cette interface et utilise le modèle objet Excel pour traiter les méthodes.  
  
 Certaines méthodes obtiennent les informations demandées à partir d’Excel, puis créent et retournent l’un des objets d’informations, par exemple l’objet `CellInformation`.  
  
 D’autres méthodes utilisent un objet d’informations fourni, recherchent le contrôle correspondant dans Excel, puis effectuent certains processus sur le contrôle. Par exemple, la méthode `ScrollIntoView` fait défiler la feuille de calcul pour que la cellule désignée soit visible.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample and ExcelCodedUIAddinHelper, communication  
 L’assembly `ExcelCodedUIAddinHelper` s’exécute dans le processus Excel et comprend la classe `UICommunicator`, qui implémente l’interface `IExcelUITestCommunication` et obtient ou définit les informations nécessaires directement à partir de l’IU Excel.  
  
 L’assembly `CodedUIExtensibilitySample` s’exécute dans le processus de test codé de l’interface utilisateur Visual Studio. Cet assembly comprend la classe `Communicator` qui ouvre un canal .NET Remoting, et fournit une propriété `Instance` qui utilise l’interface `IExcelUICommunication` pour utiliser l’objet `UICommunicator` de l’assembly `ExcelCodedUIAddinHelper` afin de passer des demandes et des objets d’informations, par exemple un objet `CellInformation`, entre les deux assemblys.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre en charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Exemple de complément Excel pour le test codé de l’interface utilisateur](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Exemple d’extension du test codé de l’interface utilisateur pour Excel](../test/sample-coded-ui-test-extension-for-excel.md)

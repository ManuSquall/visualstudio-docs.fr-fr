---
title: Exemple de complément Excel pour le test codé de l’interface utilisateur | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: aee4f7bcf827fc7d42b9c885d78b83df1ea54fd3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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

- [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Procédure pas à pas : création de votre premier complément VSTO pour Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)
- [Développement Office et SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)

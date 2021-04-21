---
title: Accès global aux objets dans les projets Office
description: Découvrez comment vous pouvez utiliser la classe Globals pour accéder à plusieurs éléments de projet différents au moment de l’exécution à partir de n’importe quel code du projet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b939131f388642b452445e0afee0f5e38d2a5195
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825535"
---
# <a name="global-access-to-objects-in-office-projects"></a>Accès global aux objets dans les projets Office
  Lorsque vous créez un projet Office, Visual Studio génère automatiquement une classe nommée `Globals` dans le projet. Vous pouvez utiliser la classe `Globals` pour accéder à plusieurs éléments de projet différents au moment de l'exécution à partir du code du projet.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Utilisation de la classe Globals
 `Globals` est une classe statique qui conserve les références à certains éléments de votre projet. Grâce à la classe `Globals` , vous pouvez accéder aux éléments suivants à partir de tout code de votre projet au moment de l'exécution :

- Classes `ThisWorkbook` et `Sheet`*n* dans un projet de modèle ou un classeur Excel. Vous pouvez accéder à ces objets à l'aide des propriétés `Globals.ThisWorkbook` et `Sheet`*n* .

- Classe `ThisDocument` dans un projet de modèle ou un document Word. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.ThisDocument` .

- `ThisAddIn`Classe dans un projet de complément VSTO. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.ThisAddIn` .

- Tous les rubans de votre projet que vous avez personnalisés en utilisant le Concepteur de ruban. Vous pouvez accéder aux rubans à l'aide de la propriété `Globals.Ribbons` . Pour plus d’informations, consultez [accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md).

- Toutes les zones de formulaire Outlook dans un projet de complément VSTO Outlook. Vous pouvez accéder aux zones de formulaire à l'aide de la propriété `Globals.FormRegions` . Pour plus d’informations, consultez [accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md).

- Un objet de fabrique qui vous permet de créer des contrôles de ruban et des éléments hôtes au moment de l'exécution dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Vous pouvez accéder à cet objet à l'aide de la propriété `Globals.Factory` . Cet objet est une instance d'une classe qui implémente l'une des interfaces suivantes :

  - [Microsoft. Office. Tools. Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft. Office. Tools. Excel. Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft. Office. Tools. Outlook. Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft. Office. Tools. Word. Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Par exemple, vous pouvez utiliser la propriété `Globals.Sheet1` pour insérer le texte dans un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> sur `Sheet1` lorsqu'un utilisateur clique sur un bouton du volet Actions dans un projet de niveau document pour Excel.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet1":::

 Le code qui tente d’utiliser la `Globals` classe avant l’initialisation du document ou du complément VSTO peut lever une exception au moment de l’exécution. Par exemple, l'utilisation de `Globals` lors de la déclaration d'une variable au niveau de la classe peut échouer, car la classe `Globals` peut ne pas être initialisée avec des références à tous les éléments hôtes avant l'instanciation de l'objet déclaré.

> [!NOTE]
> La classe `Globals` n'est jamais initialisée au moment du design, mais des instances de contrôle sont créées par le concepteur. Cela signifie que si vous créez un contrôle utilisateur qui utilise une propriété de la `Globals` classe à partir d’une classe de contrôle utilisateur, vous devez vérifier si la propriété retourne la **valeur null** avant d’essayer d’utiliser l’objet retourné.

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Élément hôte de document](../vsto/document-host-item.md)
- [Élément hôte de classeur](../vsto/workbook-host-item.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)

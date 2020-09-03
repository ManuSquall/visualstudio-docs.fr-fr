---
title: Développer des solutions Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ede09f18808eda22c747ac28e3c279fc43266bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69551576"
---
# <a name="develop-office-solutions"></a>Développer des solutions Office
  Après avoir conçu un projet à l'aide des Outils de développement Office dans Visual Studio et configuré les fichiers projet, vous pouvez vous concentrer sur l'implémentation du code et de l'interface utilisateur personnalisée.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Modèle de programmation de solutions Office
 Le modèle objet Office expose divers objets par rapport auxquels vous pouvez programmer. Quand vous programmez des solutions Office avec du code managé, vous écrivez du code qui utilise les types des assemblys PIA (Primary Interop Assembly) Office. Dans les solutions que vous créez à l'aide des modèles de projet Office dans Visual Studio, vous écrivez directement le code par rapport aux classes générées dans votre projet. Pour plus d’informations, consultez [écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programmer différents types de solutions Office
 Le type de solution que vous créez détermine les fonctionnalités que vous pouvez utiliser dans votre projet. Par exemple, vous pouvez ajouter des contrôles Windows Forms et des contrôles Office étendus (appelés *contrôles hôtes*) aux personnalisations au niveau du document en faisant glisser des éléments depuis la **Boîte à outils** dans Visual Studio au moment du design. Cependant, si vous développez un complément VSTO, vous pouvez ajouter ces types de contrôles seulement aux documents au moment de l'exécution en écrivant du code.

 Pour plus d'informations sur les fonctionnalités spécifiques aux différents types de solutions, consultez les rubriques suivantes :

- [Programmez les compléments VSTO](../vsto/programming-vsto-add-ins.md).

- [Programmez les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

  Pour obtenir des informations générales qui vous aideront à planifier vos solutions et procédures Office pour vous aider à créer des projets, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)|Décrit les différents aspects de l'écriture de code dans les solutions Office.|
|[Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)|Fournit une vue d'ensemble du modèle de programmation des compléments VSTO et des tâches de programmation connexes.|
|[Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)|Fournit une vue d'ensemble du modèle de programmation des personnalisations au niveau du document et des tâches de programmation connexes.|
|[Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)|Décrit les différentes façons de personnaliser l'interface utilisateur des applications Office à l'aide de compléments VSTO et de personnalisations au niveau du document.|
|[Données dans les solutions Office](../vsto/data-in-office-solutions.md)|Décrit les différentes façons dont vous pouvez utiliser les données dans les solutions Office, telles que la liaison de données à des contrôles et la mise en cache de données dans des personnalisations au niveau du document.|
|[Impact de l’enregistrement automatique sur les solutions Office](./how-autosave-impacts-office-solutions.md)|Décrit les ajustements que vous devrez peut-être apporter aux solutions Office lorsque l’enregistrement automatique est activé.|
|[Résoudre les problèmes des solutions Office](../vsto/troubleshooting-office-solutions.md)|Fournit des conseils pour résoudre les problèmes courants que vous pouvez rencontrer lors de la création de solutions Office.|
|[Prise en charge des threads dans Office](../vsto/threading-support-in-office.md)|Fournit une vue d'ensemble de l'utilisation de plusieurs threads dans les solutions Office.|
|[Accessibilité dans les projets Office](../vsto/accessibility-in-office-projects.md)|Décrit les fonctionnalités d'accessibilité disponibles dans les solutions Office.|

## <a name="see-also"></a>Voir aussi
- [Comment : créer et modifier des propriétés de document personnalisées](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Comment : lire et écrire dans les propriétés d’un document](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Comment : cibler l’interface utilisateur multilingue d’Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Procédure pas à pas : créer votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procédure pas à pas : créer votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Procédure pas à pas : créer votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Procédure pas à pas : créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Procédure pas à pas : créer votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

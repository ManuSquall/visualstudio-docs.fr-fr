---
title: Écrire du code dans les solutions Office
description: Apprenez à écrire du code dans des solutions Microsoft Office et découvrez la façon dont les modèles objet Office sont exposés au code managé.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea589cb4406a383876b1f16721f18fc48ebadd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526025"
---
# <a name="write-code-in-office-solutions"></a>Écrire du code dans les solutions Office
  Certains aspects de l'écriture de code dans les projets Office diffèrent des autres types de projets dans Visual Studio. La plupart de ces différences sont liées à la façon dont les modèles objet Office sont exposés au code managé. Les autres différences portent sur la conception des projets Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Code managé et programmation Office
 Automation est la technologie clé qui permet de créer une solution Microsoft Office intégrée. Elle fait partie de la technologie COM (Component Object Model). Automation rend possible l'utilisation de code pour créer et contrôler les objets logiciel qui sont exposés par une application, une DLL ou un contrôle ActiveX prenant en charge les interfaces de programmation appropriées.

### <a name="understand-primary-interop-assemblies"></a>Comprendre les assemblys PIA
 Les applications Microsoft Office exposent une grande part de leurs fonctionnalités à Automation. Toutefois, vous ne pouvez pas utiliser du code managé (notamment Visual Basic ou C#) directement pour automatiser des applications Office. Pour automatiser des applications Office avec du code managé, vous devez utiliser les assemblys PIA (Primary Interop Assembly) d'Office. Ces assemblys permettent au code managé d'interagir avec le modèle objet COM des applications Office.

 Chaque application Microsoft Office possède un assembly PIA. Quand vous créez un projet Office dans Visual Studio, une référence au PIA approprié est automatiquement ajoutée au projet. Pour automatiser les fonctionnalités d'autres applications Office à partir du projet, vous devez ajouter cette référence manuellement. Pour plus d’informations, consultez [Comment : cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Utiliser les assemblys PIA au moment du design et de l’exécution
 Pour que vous puissiez effectuer la plupart des tâches de développement, les assemblys PIA d'Office doivent être installés et inscrits dans le Global Assembly Cache de votre ordinateur de développement. Pour plus d’informations, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Sur les ordinateurs des utilisateurs finaux, les assemblys PIA d'Office ne sont pas nécessaires pour exécuter les solutions Office ciblant [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure. Pour plus d’informations, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Utiliser des types dans les assemblys PIA
 Les assemblys PIA d'Office fournissent une combinaison de types qui exposent le modèle objet des applications Office et d'autres types d'infrastructure qui ne sont pas prévus pour être utilisés directement dans votre code. Pour obtenir une vue d’ensemble des types dans les assemblys PIA Office, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/office-12/ms247299\(v\=office.12\))) d’Office.

 Étant donné que les types des assemblys PIA d'Office correspondent aux types des modèles objet COM, la façon dont vous utilisez ces types diffère souvent des autres types managés. Par exemple, le mode d'appel des méthodes possédant des paramètres optionnels dans un assembly PIA d'Office dépend du langage de programmation utilisé dans le projet. Pour plus d'informations, voir les rubriques suivantes :

- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md).

- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Modèle de programme des projets Office
 Tous les projets Office incluent une ou plusieurs classes générées qui fournissent le point d'entrée de votre code. Ces classes fournissent également l'accès au modèle objet de l'application hôte, ainsi qu'aux fonctionnalités telles que les volets Actions et les volets de tâches personnalisés.

### <a name="understand-the-generated-classes"></a>Comprendre les classes générées
 Dans les projets de niveau document pour Excel et Word, la classe générée ressemble à un objet de niveau supérieur du modèle objet de l'application. Par exemple, la classe `ThisDocument` générée d'un projet de document Word fournit les mêmes membres que la classe <xref:Microsoft.Office.Interop.Word.Document> du modèle objet Word. Pour plus d’informations sur les classes générées dans les projets au niveau du document, consultez [programmation des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).

 Les projets de complément VSTO fournissent une classe générée nommée `ThisAddIn`. Cette classe ne ressemble pas à une classe du modèle objet de l'application hôte. Au lieu de cela, cette classe représente le complément VSTO proprement dit et fournit des membres que vous pouvez utiliser pour accéder au modèle objet de l’application hôte et accéder à d’autres fonctionnalités disponibles pour les compléments VSTO. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

 Toutes les classes générées dans les projets Office incluent des gestionnaires d'événements `Startup` et `Shutdown` . Pour commencer à écrire du code, vous ajoutez généralement ce code à ces gestionnaires d'événements. Pour initialiser votre complément VSTO, vous pouvez ajouter du code au gestionnaire d’événements `Startup` . Pour nettoyer les ressources utilisées par votre complément VSTO, vous pouvez ajouter du code au gestionnaire d’événements `Shutdown` . Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Accéder aux classes générées au moment de l’exécution
 Quand une solution Office est chargée, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instancie chacune des classes générées dans votre projet. Vous pouvez accéder à ces objets directement du code de votre projet à l'aide de la classe `Globals` . Par exemple, vous pouvez utiliser la `Globals` classe pour appeler du code dans la `ThisAddIn` classe à partir d’un gestionnaire d’événements d’un bouton de ruban dans un complément VSTO.

 Pour plus d’informations, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Considérations relatives aux espaces de noms dans les solutions Office
 Vous ne pouvez pas modifier l' *espace de noms par défaut* (ou l' *espace de noms racine* dans Visual Basic) dans un projet Office existant. L'espace de noms par défaut correspondra toujours au nom du projet que vous avez spécifié lors de sa création. Si vous renommez votre projet, l'espace de noms par défaut ne change pas. Pour plus d’informations sur l’espace de noms par défaut dans les projets, consultez [page application, concepteur de projets &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) et [page application, concepteur de projets &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Modifier l’espace de noms des classes d’élément hôte dans les projets C#
 Les classes d'élément hôte (par exemple, `ThisAddIn`, `ThisWorkbook`et `ThisDocument` ) ont leurs propres espaces de noms dans les projets Office Visual C#. Par défaut, l'espace de noms des éléments hôtes dans votre projet correspond au nom de projet que vous avez spécifié lors de la création de ce dernier.

 Pour modifier l'espace de noms des éléments hôtes dans un projet Office Visual C#, utilisez la propriété **Espace de noms de l'élément hôte** . Pour plus d’informations, consultez [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Langages de programmation pris en charge dans les projets Office
 Les modèles de projet Office dans Visual Studio prennent uniquement en charge les langages de programmation Visual Basic et Visual C#. Par conséquent, ces modèles de projet sont disponibles uniquement sous les nœuds **Visual Basic** et **Visual C#** de la boîte de dialogue **Nouveau projet** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Choix du langage et programmation Office
 Microsoft Office et Visual Basic pour Applications (VBA) ont été développés pour fonctionner ensemble afin d'optimiser le workflow de la personnalisation d'application. Visual Basic a hérité certains de ces développements, comme la prise en charge des paramètres optionnels. L'utilisation de ces paramètres vous permet d'appeler certaines méthodes dans les assemblys PIA (Primary Interop Assembly) de Microsoft Office en ayant moins de code à écrire qu'avec Visual C#.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programme avec Visual Basic et Visual C# dans les solutions Office
 Vous pouvez créer des solutions Office à l'aide de Visual Basic ou Visual C#. Étant donné que les modèles objet de Microsoft Office ont été conçus pour être utilisés avec Microsoft Visual Basic pour Applications (VBA), les développeurs en Visual Basic peuvent facilement travailler avec les objets exposés par les applications Microsoft Office. Les développeurs en Visual C# peuvent utiliser la plupart des fonctionnalités disponibles pour les développeurs en Visual Basic, sauf dans certains cas où ils doivent écrire du code supplémentaire pour pouvoir utiliser les modèles objet d'Office. Il existe également quelques différences entre les fonctionnalités de programmation de base dans le développement Office et le code managé écrit en Visual Basic et Visual C#.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Principales différences entre Visual Basic et Visual C #
<!-- markdownlint-enable MD003 MD020 -->

Le tableau suivant indique les principales différences entre Visual Basic et Visual C# dans le développement Office.

|Fonctionnalité|Description|Prise en charge dans Visual Basic|Prise en charge dans Visual C#|
|-------------|-----------------|--------------------------|------------------------|
|Paramètres facultatifs|De nombreuses méthodes Microsoft Office possèdent des paramètres qui ne sont pas obligatoires quand vous les appelez. Si aucune valeur n'est passée comme paramètre, une valeur par défaut est utilisée.|Visual Basic prend en charge les paramètres optionnels.|Visual C# prend en charge les paramètres optionnels dans la plupart des cas. Pour plus d’informations, consultez [paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md).|
|Passage de paramètres par référence|Dans la plupart des assemblys PIA (Primary Interop Assembly) de Microsoft Office, les paramètres optionnels peuvent être passés par valeur. Toutefois, dans certains assemblys PIA, les paramètres optionnels qui acceptent les types référence doivent être passés par référence.<br /><br /> Pour plus d’informations sur les paramètres de type valeur et référence, consultez [passer des arguments par valeur et par référence &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pour Visual Basic) et [paramètres Pass &#40;guide de programmation&#35; C ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)&#41;.|Le passage des paramètres par référence est possible sans codage supplémentaire. Le compilateur Visual Basic passe automatiquement les paramètres par référence nécessaires.|Le plus souvent, le compilateur Visual C# passe automatiquement les paramètres par référence nécessaires. Pour plus d’informations, consultez [paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md).|
|Propriétés paramétrables|Certaines propriétés acceptent des paramètres et agissent comme des fonctions en lecture seule.|Visual Basic prend en charge les propriétés qui acceptent des paramètres.|Visual C# prend en charge les propriétés qui acceptent des paramètres.|
|Liaison tardive|La liaison tardive implique de déterminer les propriétés d'objets au moment de l'exécution, au lieu d'effectuer un cast de variables en type d'objet au moment du design.|Visual Basic effectue la liaison tardive quand **Option Strict** est désactivé. Si **Option Strict** est activé, vous devez convertir explicitement les objets et utiliser les types figurant dans l'espace de noms <xref:System.Reflection> pour accéder aux membres à liaison tardive. Pour plus d’informations, consultez [liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).|Visual C# effectue la liaison tardive dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Pour plus d’informations, consultez [liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Principales différences entre le développement Office et le code managé
 Le tableau suivant indique les principales différences entre le développement Office et le code managé écrit en Visual Basic ou Visual C#.

|Fonctionnalité|Description|Prise en charge dans Visual Basic et Visual C#|
|-------------|-----------------|-----------------------------------------|
|Index de tableau|La limite de tableau inférieure de collections dans les applications Microsoft Office commencent par 1. Visual Basic et Visual C# utilisent des tableaux basés sur 0. Pour plus d’informations, consultez [tableaux &#40;Guide de programmation C&#35;&#41;](/dotnet/csharp/programming-guide/arrays/index) et [tableaux dans Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Pour accéder au premier élément d'une collection dans le modèle objet d'une application Microsoft Office, utilisez l'index 1 au lieu de 0.|

## <a name="see-also"></a>Voir aussi

- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Événements dans les projets Office](../vsto/events-in-office-projects.md)
- [Comment : cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Liaison tardive dans les solutions Office](../vsto/late-binding-in-office-solutions.md)
- [Développement collaboratif de solutions Office](../vsto/collaborative-development-of-office-solutions.md)

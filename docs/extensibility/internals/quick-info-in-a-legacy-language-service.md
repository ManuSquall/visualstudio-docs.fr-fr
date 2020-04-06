---
title: Informations rapides dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705941"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informations rapides dans un service de langage hérité
IntelliSense Quick Info affiche des informations sur un identifiant dans la source lorsque l’utilisateur place le caret dans l’identifiant et sélectionne **Des informations rapides** dans le menu **IntelliSense** ou tient le curseur de souris sur l’identifiant. Cela provoque un conseil d’outil à apparaître avec des informations sur l’identifiant. Ces informations se composent généralement du type d’identifiant. Lorsque le moteur de débogé est actif, ces informations peuvent inclure la valeur actuelle. Le moteur de débogé fournit des valeurs d’expression, tandis que le service linguistique ne gère que des identificateurs.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Procédure pas à pas : Afficher quickInfo Tooltips](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

 Les cours de service linguistique du cadre de forfait géré (MPF) fournissent un soutien complet pour l’affichage de l’astuce de l’outil IntelliSense Quick Info. Tout ce que vous avez à faire est de fournir le texte pour être affiché et activer la fonction d’information rapide.

 Le texte à afficher est obtenu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> en appelant le parseur de <xref:Microsoft.VisualStudio.Package.ParseReason>méthode avec une valeur de raison d’analyse de . Cette raison indique au analyseur d’obtenir les informations de type (ou tout ce qui est approprié <xref:Microsoft.VisualStudio.Package.ParseRequest> pour être affiché dans la pointe de l’outil Quick Info) pour l’identifiant à l’emplacement spécifié dans l’objet. L’objet <xref:Microsoft.VisualStudio.Package.ParseRequest> est ce <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> qui a été transmis à la méthode.

 L’analyseur doit tout analyser jusqu’à <xref:Microsoft.VisualStudio.Package.ParseRequest> la position dans l’objet afin de déterminer les types de tous les identificateurs. Ensuite, le parseur doit obtenir l’identifiant à l’emplacement de demande d’analyse. Enfin, le parseur doit passer les données de <xref:Microsoft.VisualStudio.Package.AuthoringScope> pointe de l’outil associées <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> à cet identifiant à l’objet afin que l’objet puisse renvoyer le texte de la méthode.

## <a name="enabling-the-quick-info-feature"></a>Permettre la fonction d’information rapide
 Pour activer la fonction Quick `CodeSense` Info, vous devez définir les paramètres et `QuickInfo` les paramètres désignés de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Ces attributs <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> définissez les propriétés et <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> les propriétés.

## <a name="implementing-the-quick-info-feature"></a>Mise en œuvre de la fonction d’information rapide
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gère l’opération IntelliSense Quick Info. Lorsque <xref:Microsoft.VisualStudio.Package.ViewFilter> la classe <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> reçoit la commande, la classe appelle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> la méthode avec la raison d’analyse et l’emplacement de la caret au moment où la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande a été envoyée. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyseur de méthode doit ensuite analyser la source jusqu’à l’emplacement donné, puis analyser l’identifiant à l’endroit donné pour déterminer ce qu’il faut afficher dans la pointe de l’outil Quick Info.

 La plupart des analyseurs font un analyse initial de l’ensemble du fichier source et stockent les résultats dans un arbre d’analyse. L’analyse complète est effectuée <xref:Microsoft.VisualStudio.Package.ParseReason> lorsque <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> elle est transmise à la méthode. D’autres types d’analyse peuvent alors utiliser l’arbre de parse pour obtenir l’information désirée.

 Par exemple, la valeur de <xref:Microsoft.VisualStudio.Package.ParseReason> raison d’analyse de peut trouver l’identifiant à l’emplacement source et le chercher dans l’arbre d’analyse pour obtenir l’information de type. Ces informations de type <xref:Microsoft.VisualStudio.Package.AuthoringScope> sont ensuite transmises <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> à la classe, et sont retournées par la méthode.

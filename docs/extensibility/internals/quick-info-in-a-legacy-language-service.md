---
title: Info Express dans un service de langage hérité | Microsoft Docs
description: En savoir plus sur la prise en charge de l’opération Info Express IntelliSense pour afficher des informations sur un identificateur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90cab5683c7a13aec25b15d75da0117beee34721
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060885"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Informations rapides dans un service de langage hérité
Info Express IntelliSense affiche des informations sur un identificateur dans la source lorsque l’utilisateur place le signe insertion dans l’identificateur et sélectionne **Info Express** dans le menu **IntelliSense** ou maintient le curseur de la souris sur l’identificateur. Cela entraîne l’affichage d’une info-bulle avec des informations sur l’identificateur. Ces informations se composent généralement du type d’identificateur. Lorsque le moteur de débogage est actif, ces informations peuvent inclure la valeur actuelle. Le moteur de débogage fournit des valeurs d’expression, tandis que le service de langage gère uniquement les identificateurs.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour plus d’informations, consultez [procédure pas à pas : affichage des info-bulles Info-bulles](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

 Les classes du service de langage de l’infrastructure de package managé (MPF) fournissent une prise en charge complète de l’affichage de l’info-bulle IntelliSense Info Express. Il vous suffit de fournir le texte à afficher et d’activer la fonctionnalité Info Express.

 Le texte à afficher est obtenu en appelant l' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec une valeur de raison d’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> . Cette raison indique à l’analyseur d’obtenir les informations de type (ou tout ce qui est approprié à afficher dans l’info-bulle de l’outil Info Express) pour l’identificateur à l’emplacement spécifié dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. L' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est ce qui a été passé à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode.

 L’analyseur doit tout analyser jusqu’à la position dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet afin de déterminer les types de tous les identificateurs. Ensuite, l’analyseur doit obtenir l’identificateur à l’emplacement de la demande d’analyse. Enfin, l’analyseur doit passer les données d’info-bulle associées à cet identificateur à l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet afin que l’objet puisse retourner le texte de la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> méthode.

## <a name="enabling-the-quick-info-feature"></a>Activation de la fonctionnalité Info Express
 Pour activer la fonctionnalité Info Express, vous devez définir les `CodeSense` `QuickInfo` paramètres nommés et de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Ces attributs définissent les <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Propriétés et.

## <a name="implementing-the-quick-info-feature"></a>Implémentation de la fonctionnalité Info Express
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gère l’opération Info Express IntelliSense. Lorsque la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe reçoit la <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande, la classe appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode avec la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason> et l’emplacement du signe insertion au moment de l' <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> envoi de la commande. L' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode doit ensuite analyser la source jusqu’à l’emplacement donné, puis analyser l’identificateur à l’emplacement donné pour déterminer ce qui doit être affiché dans l’info-bulle de l’outil Info Express.

 La plupart des analyseurs effectuent une analyse initiale de l’intégralité du fichier source et stockent les résultats dans une arborescence d’analyse. L’analyse complète est exécutée lorsque <xref:Microsoft.VisualStudio.Package.ParseReason> est passé à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode. D’autres types d’analyse peuvent ensuite utiliser l’arborescence d’analyse pour obtenir les informations souhaitées.

 Par exemple, la valeur de raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> peut trouver l’identificateur à l’emplacement source et le Rechercher dans l’arborescence d’analyse pour obtenir les informations de type. Ces informations de type sont ensuite passées à la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe et sont retournées par la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> méthode.

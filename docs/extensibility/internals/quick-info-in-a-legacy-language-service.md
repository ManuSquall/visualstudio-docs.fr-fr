---
title: Info express dans un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="quick-info-in-a-legacy-language-service"></a>Info express dans un Service de langage hérité
Info express IntelliSense affiche des informations d’un identificateur de la source lorsque l’utilisateur place le point d’insertion dans l’identificateur et sélectionne **Info Express** à partir de la **IntelliSense** menu ou détient la souris curseur sur l’identificateur. Cela provoque une info-bulle à afficher des informations sur l’identificateur. Ces informations se composent généralement de type identificateur. Lorsque le moteur de débogage est actif, ces informations peuvent inclure la valeur actuelle. Le moteur de débogage fournit des valeurs de l’expression, tandis que le service de langage gère uniquement des identificateurs.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [procédure pas à pas : affichage des info-bulles Info Express](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Les classes de service de langage managé package framework (MPF) fournissent la prise en charge complète pour l’affichage des info-bulle Info express IntelliSense. Il vous est de fournir le texte pour afficher et activer la fonctionnalité info Express.  
  
 Le texte à afficher est obtenu en appelant le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec une valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cela indique à l’analyseur pour obtenir les informations de type (ou tout ce qui est approprié à afficher dans l’info-bulle Info express) pour l’identificateur à l’emplacement spécifié dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est ce qui a été passé à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode).  
  
 L’analyseur doit analyser tous les éléments jusqu'à la position dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet afin de déterminer les types de tous les identificateurs. Puis l’analyseur doit obtenir l’identificateur à l’emplacement de demande d’analyse. Enfin, l’analyseur doit passer les données de conseil outil associées à cet identificateur pour le <xref:Microsoft.VisualStudio.Package.AuthoringScope> afin que cet objet puisse retourner le texte à partir de l’objet le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> (méthode).  
  
## <a name="enabling-the-quick-info-feature"></a>L’activation de la fonctionnalité Info express  
 Pour activer la fonctionnalité Info express, vous devez définir le `CodeSense` et `QuickInfo` les paramètres nommés de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Ces attributs définissent les <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> et <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> propriétés.  
  
## <a name="implementing-the-quick-info-feature"></a>L’implémentation de la fonctionnalité Info express  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gère l’opération Info express IntelliSense. Lorsque le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe reçoit le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande, la classe appelle la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> et l’emplacement du signe insertion au moment le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande a été envoyée. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de la méthode doit ensuite analyser la source jusqu'à l’emplacement donné, puis analyse l’identificateur à l’emplacement donné pour déterminer les éléments à afficher dans l’info-bulle Info Express.  
  
 La plupart des analyseurs, effectuer une analyse initiale de l’intégralité du fichier source et stocker les résultats dans une arborescence d’analyse. L’analyse complète est effectuée lorsque <xref:Microsoft.VisualStudio.Package.ParseReason> est passé à <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode). Autres types de l’analyse peuvent ensuite utiliser l’arborescence d’analyse pour obtenir les informations souhaitées.  
  
 Par exemple, la valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> peut rechercher l’identificateur à l’emplacement source et rechercher dans l’arborescence d’analyse pour obtenir les informations de type. Ces informations de type sont ensuite transmises à la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe et est retournée par le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> (méthode).
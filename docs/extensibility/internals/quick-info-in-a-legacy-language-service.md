---
title: "Infos Express dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Info express, prise en charge dans les services de langage (framework package managé)"
  - "IntelliSense, Infos Express"
  - "services de langage (framework package managé), Info express IntelliSense"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Infos Express dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Info express IntelliSense affiche des informations sur un identificateur de la source lorsque l’utilisateur place le signe insertion dans l’identificateur sélectionne **Infos** à partir de la **IntelliSense** menu ou maintient le curseur de la souris sur l’identificateur. Ainsi, une info\-bulle à afficher des informations sur l’identificateur. Ces informations se composent généralement du type d’identificateur. Lorsque le moteur de débogage est activé, ces informations peuvent inclure la valeur actuelle. Le moteur de débogage fournit des valeurs de l’expression, tandis que le service de langage gère uniquement des identificateurs.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [Procédure pas à pas : Affichage des info\-bulles Info express](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Les classes de service de langage managé package framework \(MPF\) fournissent la prise en charge complète pour l’affichage d’info\-bulle Info express IntelliSense. Il vous suffit est de fournir le texte pour afficher et activer la fonctionnalité info Express.  
  
 Le texte à afficher est obtenu en appelant le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec une valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cela indique à l’analyseur pour obtenir les informations de type \(ou tout ce qui est approprié à afficher dans l’info\-bulle Info express\) pour l’identificateur à l’emplacement spécifié dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est ce qui a été passé à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(méthode\).  
  
 L’analyseur doit analyser tous les éléments jusqu'à la position dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet afin de déterminer les types de tous les identificateurs. Puis l’analyseur doit obtenir l’identificateur à l’emplacement de demande d’analyse. Enfin, l’analyseur doit transmettre les données de conseil outil associées à cet identificateur à la <xref:Microsoft.VisualStudio.Package.AuthoringScope> afin que cet objet puisse retourner le texte à partir de l’objet du <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> \(méthode\).  
  
## L’activation de la fonctionnalité Infos Express  
 Pour activer la fonctionnalité Infos Express, vous devez définir le `CodeSense` et `QuickInfo` nommé de paramètres de le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Ces attributs définissent les <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> et <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Propriétés.  
  
## L’implémentation de la fonctionnalité Infos Express  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gère l’opération Info express IntelliSense. Lors de la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe reçoit le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande, la classe appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> et l’emplacement du signe insertion au moment le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande a été envoyée. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de la méthode doit ensuite analyser la source jusqu'à l’emplacement donné, puis analyse l’identificateur à l’emplacement donné pour déterminer les éléments à afficher dans l’info\-bulle Info Express.  
  
 La plupart des analyseurs de faire une analyse initiale de l’intégralité du fichier source et stocker les résultats dans une arborescence d’analyse. L’analyse complète est effectuée lorsque <xref:Microsoft.VisualStudio.Package.ParseReason> est transmis à <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(méthode\). Autres types d’analyse permet ensuite l’arborescence d’analyse pour obtenir les informations souhaitées.  
  
 Par exemple, la valeur de raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> peut rechercher l’identificateur à l’emplacement source et la rechercher dans l’arborescence d’analyse pour obtenir les informations de type. Ces informations de type sont ensuite transférées à la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe et est retourné par le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> \(méthode\).
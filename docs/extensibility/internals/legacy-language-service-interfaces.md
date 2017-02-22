---
title: "Interfaces de Service de langage ancien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IVsLanguageInfo"
  - "services de langage, objets"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Interfaces de Service de langage ancien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour n'importe quel langage de programmation particulier, il peut y avoir qu'une seule instance d'un service de langage à la fois.  Toutefois, un service seul langage peut servir plusieurs éditeur.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n'associe un service de langage à un éditeur particulier.  Par conséquent, lorsque vous demandez une opération de service de langage, vous devez identifier l'éditeur approprié comme paramètre.  
  
## Interfaces courantes associées à des services de langage  
 L'éditeur obtient votre service de langage en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sur le VSPackage approprié.  L'ID de service \(SID\) passé dans cet appel identifie le service de langage demandé.  
  
 Vous pouvez implémenter les interfaces principales de service de langage dans plusieurs classes séparées.  Toutefois, une approche courante consiste à implémenter les interfaces suivantes dans une classe unique :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(facultatif\)  
  
 l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> doit être implémentée sur tous les services linguistiques.  Il fournit des informations sur votre service de langage, tel que le nom localisé du langage, les extensions de nom de fichier associée au service de langage, et comment récupérer un coloriseur.  
  
## Interfaces de service de langage supplémentaire  
 D'autres interfaces peuvent être fournies avec votre service de langage.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] demande une instance séparée de ces interfaces pour chaque instance de la mémoire tampon de texte.  Par conséquent, vous devez implémenter chacune de ces interfaces sur son propre objet.  Le tableau suivant indique les interfaces qui nécessitent une instance de chaque instance de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|gère des ornements de fenêtre de code, tels que la barre déroulante.  vous pouvez obtenir cette interface à l'aide de la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  Il existe un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> par fenêtre de code.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|mots clés et séparateurs de langage de Colorizes.  vous pouvez obtenir cette interface à l'aide de la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> .  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> est appelé au temps de peinture.  Évitez le travail nécessitant de nombreuses ressources de calcul à l'intérieur de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ou les performances peuvent souffrir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fournit des info\-bulles de paramètre Intellisense.  Lorsque le service de langage reconnaît un caractère qui indique ces données de méthode doit être rendu, par exemple une parenthèse ouvrante, il appelle la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> pour informer l'affichage de texte que le service de langage est prêt à afficher des informations sur les paramètres une info\-bulle.  Les appels d'affichage de texte ensuite au service de langage à l'aide de les méthodes d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface pour obtenir les informations requises pour afficher l'info\-bulle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fournit la saisie semi\-automatique des instructions Intellisense.  Lorsque le service de langage est prêt à afficher une liste de saisie semi\-automatique, elle appelle la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> sur l'affichage de texte.  Les appels d'affichage de texte et au service de langage à l'aide de méthodes sur l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Autorise la modification de l'affichage de texte à l'aide de le gestionnaire de commandes.  la classe dans laquelle vous implémentez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> doit également implémenter l'interface d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  L'affichage de texte récupère l'objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> en interrogeant l'objet d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passé dans la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  Il doit y avoir un objet d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> pour chaque affichage.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Arrête les commandes ces les types d'utilisateur de la fenêtre de code.  Sortie écran de votre implémentation d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour fournir des informations personnalisées d'avancement et la modification de vue<br /><br /> pour passer votre objet d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> à l'affichage de texte, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>d'appel.|  
  
## Voir aussi  
 [Développement d'un Service de langage](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Liste de vérification : Création d’un Service de langage hérité](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
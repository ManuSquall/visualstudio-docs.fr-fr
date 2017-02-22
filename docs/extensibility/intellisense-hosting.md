---
title: "H&#233;bergement d&#39;IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - IntelliSense d'hébergement"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# H&#233;bergement d&#39;IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio active héberger Intellisense.  L'hébergement d'IntellSense vous permet de fournir Intellisense pour le code qui n'est pas hébergé par l'éditeur de texte Visual Studio.  
  
## Intellisense qui héberge l'utilisation  
 Dans Visual Studio, tout code qui a accès à un jeu de saisies semi\-automatiques et dans une mémoire tampon de texte peut obtenir des fenêtres d'Intellisense n'importe où dans l'interface \(UI\) utilisateur.  Certains scénarios d'exemple de procédure sont saisie semi\-automatique dans la fenêtre d' **Espion** ou dans le champ de la condition d'une fenêtre de propriétés.  
  
### interfaces d'implémentation  
  
#### IVsIntellisenseHost  
 Tout composant de l'interface utilisateur qui héberge des fenêtres indépendantes Intellisense doit prendre en charge l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> .  Le principal affichage de texte par défaut de l'éditeur inclut une implémentation magasin d'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> pour conserver les fonctionnalités actuelles Intellisense.  Pour la plupart, les méthodes d'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> représentent un sous\-ensemble de ce qui est implémenté dans l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  Le sous\-ensemble inclut la gestion d'Intellisense interface utilisateur, la manipulation du signe insertion et de sélection, et la fonctionnalité simple de remplacement de texte.  En outre, l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> active Intellisense séparé « rubrique » et « contexte » afin qu'Intellisense puisse être fourni pour les rubriques qui n'existent pas directement dans la mémoire tampon de texte qui est utilisée pour le contexte.  
  
#### IVsIntellisenseHost.GetHostFlags  
 Un fournisseur d'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> doit implémenter la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> pour permettre à un client de déterminer le type d'Intellisense comporte prend en charge hôte.  
  
 les balises d'hôte, définies dans [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sont résumées ci\-dessous.  
  
|Balise d'hôte Intellisense|Description|  
|--------------------------------|-----------------|  
|IHF\_READONLYCONTEXT|Définition de cet indicateur signifie que la mémoire tampon de contexte est en lecture seule et la modification se produit uniquement dans le texte soumis.|  
|IHF\_NOSEPERATESUBJECT|Définition de cet indicateur signifie qu'il n'existe aucun rubrique séparée Intellisense.  La rubrique existe dans la mémoire tampon de contexte, tel que dans le système traditionnel d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Intellisense.|  
|IHF\_SINGLELINESUBJECT|Définition de cet indicateur signifie que la rubrique n'est pas capable multiligne, par exemple dans une modification de ligne unique dans la fenêtre d' **Espion** .|  
|IHF\_FORCECOMMITTOCONTEXT|Si elle est définie et la mémoire tampon de contexte sera mise à jour, l'hôte active l'indicateur de lecture seule dans la mémoire tampon de contexte à ignorer et des modifications pour continuer.|  
|IHF\_OVERTYPE|Changer \(dans la rubrique ou le contexte\) doit être effectuée dans refrappent mode.|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit et IVsIntellisenseHost.AfterCompletorCommit  
 Ces méthodes de rappel sont appelées par la fenêtre d'achèvement avant et après que le texte soit validé, pour activer le prétraitement et le post\-traitement.  
  
#### IVsIntellisenseCompletor  
 L'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> est une version Co\-creatable de la fenêtre standard d'achèvement qui est utilisée par l'environnement de développement intégré \(IDE\) \(IDE\).  Toute interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> peut rapidement implémenter Intellisense à l'aide de cette interface de completor.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
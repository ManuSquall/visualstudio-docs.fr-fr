---
title: "IntelliSense hébergement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850e4b2ef6d455bb141827fa125c4c7c6860b652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense-hosting"></a>Hébergement d’IntelliSense
Visual Studio permet à IntelliSense d’hébergement. IntellSense hébergement vous permet de vous fournissez IntelliSense pour le code qui n’est pas hébergé par l’éditeur de texte Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilisation d’hébergement IntelliSense  
 Dans Visual Studio, tout code qui a accès à un ensemble de saisie semi-automatique et d’une mémoire tampon de texte peut procurer IntelliSense depuis n’importe où dans l’interface utilisateur (IU). Des exemples de scénarios de ce sont de saisie semi-automatique dans le **espion** fenêtre ou dans le champ de la condition d’une fenêtre de propriétés du point d’arrêt.  
  
### <a name="implementation-interfaces"></a>Interfaces d’implémentation  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Tout composant d’interface utilisateur qui héberge les fenêtres publicitaires IntelliSense doit prendre en charge la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface. L’affichage de texte de l’éditeur principal par défaut inclut une action <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implémentation pour conserver les fonctionnalités IntelliSense en cours de l’interface. Dans la plupart des cas, les méthodes de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface représentent un sous-ensemble de ce qui est implémenté sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Ce sous-ensemble inclut IntelliSense UI gestion, du point d’insertion et manipulation de sélection et les fonctionnalités de remplacement de texte simple. En outre, le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface permet distinct IntelliSense « subject » et « contexte » afin qu’IntelliSense peut être fournie pour les objets qui n’existent pas directement dans la mémoire tampon de texte qui est utilisé pour le contexte.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> fournisseur d’interface doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> méthode pour permettre à un client déterminer quel type d’IntelliSense propose l’hôte prend en charge.  
  
 Les indicateurs de l’hôte, définis dans [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sont résumées ci-dessous.  
  
|Indicateur de l’hôte d’IntelliSense|Description|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Choix de cette indicateur signifie que la mémoire tampon de contexte est en lecture seule et de modification se produit uniquement dans le texte de l’objet.|  
|IHF_NOSEPERATESUBJECT|Choix cet indicateur signifie que, il n’est pas d’objet IntelliSense distinct. L’objet existe dans la mémoire tampon de contexte, telles que traditionnel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> système IntelliSense.|  
|IHF_SINGLELINESUBJECT|Choix de cette indicateur signifie que l’objet n’est pas multiligne capable, par exemple, dans une seule ligne d’édition dans le **espion** fenêtre.|  
|IHF_FORCECOMMITTOCONTEXT|Si cet indicateur est défini et que la mémoire tampon de contexte doit être mis à jour, l’hôte Active l’indicateur en lecture seule sur la mémoire tampon de contexte doivent être ignorés et les modifications pour continuer.|  
|IHF_OVERTYPE|Modification (dans l’objet ou le contexte) doit être effectuée en mode Refrappe.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit et IVsIntellisenseHost.AfterCompletorCommit  
 Ces méthodes de rappel sont appelées par la fenêtre de saisie semi-automatique avant et après que le texte est validé, pour activer le pré-traitement et post-traitement.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interface est une version peut être créée conjointement de la fenêtre de saisie semi-automatique standard qui est utilisée par l’environnement de développement intégré (IDE). N’importe quel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface peut implémenter rapidement IntelliSense à l’aide de cette interface completor.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
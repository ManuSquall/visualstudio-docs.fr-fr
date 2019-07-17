---
title: Hébergement IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203900"
---
# <a name="intellisense-hosting"></a>Hébergement d’IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio permet l’hébergement d’IntelliSense. Dans IntelliSense hébergement permet de vous fournir IntelliSense pour le code qui n’est pas hébergée par l’éditeur de texte Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilisation d’hébergement IntelliSense  
 Dans Visual Studio, tout code qui a accès à un jeu de saisies semi-automatiques et une mémoire tampon de texte peut obtenir IntelliSense windows depuis n’importe où dans l’interface utilisateur (IU). Des exemples de scénarios de ce sont de saisie semi-automatique dans le **espion** fenêtre ou dans le champ de la condition d’une fenêtre de propriétés de point d’arrêt.  
  
### <a name="implementation-interfaces"></a>Interfaces de l’implémentation  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Tout composant de l’interface utilisateur qui héberge les fenêtres publicitaires IntelliSense doit prendre en charge la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface. L’affichage de texte de l’éditeur par défaut core inclut un stock <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implémentation pour conserver la fonctionnalité IntelliSense en cours de l’interface. La plupart du temps, les méthodes de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface représentent un sous-ensemble de ce qui est implémenté sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le sous-ensemble inclut IntelliSense UI gestion, du signe insertion et manipulation de sélection et les fonctionnalités de remplacement de texte simple. En outre, le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface permet distinct IntelliSense « subject » et « contexte » afin qu’IntelliSense peut être fourni pour des sujets qui n’existent pas directement dans la mémoire tampon de texte qui est utilisé pour le contexte.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> fournisseur de l’interface doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> méthode pour permettre à un client déterminer quel type d’IntelliSense propose l’hôte prend en charge.  
  
 Les indicateurs d’hôte, définis dans [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sont résumés ci-dessous.  
  
|Indicateur de l’hôte IntelliSense|Description|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Paramètre cela signifie d’indicateur que la mémoire tampon de contexte est en lecture seule et de modification se produit uniquement dans le texte de l’objet.|  
|IHF_NOSEPERATESUBJECT|La définition cela signifie d’indicateur qui il est sans objet IntelliSense distinct. L’objet existe dans la mémoire tampon de contexte, telles que le traditionnel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> système IntelliSense.|  
|IHF_SINGLELINESUBJECT|Paramètre cela signifie d’indicateur qui n’est pas le sujet multiligne capable, par exemple, dans une seule ligne modifier dans le **espion** fenêtre.|  
|IHF_FORCECOMMITTOCONTEXT|Si cet indicateur est défini et que la mémoire tampon de contexte doit être mis à jour, l’hôte Active l’indicateur en lecture seule sur la mémoire tampon de contexte doivent être ignorés et les modifications pour continuer.|  
|IHF_OVERTYPE|Modification (dans l’objet ou le contexte) doit être effectuée en mode Refrappe.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit et IVsIntellisenseHost.AfterCompletorCommit  
 Ces méthodes de rappel sont appelées par la fenêtre de saisie semi-automatique avant et après que le texte est validé, pour activer le prétraitement et le post-traitement.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interface est une version pouvant être créée conjointement de la fenêtre de saisie semi-automatique standard qui est utilisée par l’environnement de développement intégré (IDE). N’importe quel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface peut implémenter rapidement IntelliSense à l’aide de cette interface completor.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop>

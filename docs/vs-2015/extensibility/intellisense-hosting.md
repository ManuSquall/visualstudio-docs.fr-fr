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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203900"
---
# <a name="intellisense-hosting"></a>Hébergement d’IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio active l’hébergement IntelliSense. L’hébergement IntelliSense vous permet de fournir IntelliSense pour du code qui n’est pas hébergé par l’éditeur de texte Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Utilisation de l’hébergement IntelliSense  
 Dans Visual Studio, tout code qui a accès à un jeu de saisies semi-automatiques et à une mémoire tampon de texte peut obtenir des fenêtres IntelliSense depuis n’importe quel endroit de l’interface utilisateur (IU). Quelques exemples de scénarios de cette opération sont terminés dans la fenêtre **Espion** ou dans le champ condition d’une fenêtre de propriétés de point d’arrêt.  
  
### <a name="implementation-interfaces"></a>Interfaces d’implémentation  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Tout composant d’interface utilisateur qui héberge des fenêtres contextuelles IntelliSense doit prendre en charge l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface. L’affichage de texte par défaut de l’éditeur principal comprend une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implémentation de l’interface stock pour conserver les fonctionnalités IntelliSense actuelles. Pour l’essentiel, les méthodes de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface représentent un sous-ensemble de ce qui est implémenté sur l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. Le sous-ensemble comprend la gestion de l’interface utilisateur IntelliSense, les manipulations de signe insertion et de sélection, ainsi que la fonctionnalité de remplacement de texte simple. En outre, l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface active des « Subject » et « Context » IntelliSense distincts, afin qu’IntelliSense puisse être fourni pour les sujets qui n’existent pas directement dans la mémoire tampon de texte utilisée pour le contexte.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> fournisseur d’interface doit implémenter la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> méthode pour permettre à un client de déterminer quel type de fonctionnalités IntelliSense est pris en charge par l’hôte.  
  
 Les indicateurs d’hôte, définis dans [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sont résumés ci-dessous.  
  
|Indicateur d’hôte IntelliSense|Description|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|La définition de cet indicateur signifie que la mémoire tampon de contexte est en lecture seule et que la modification se produit uniquement dans le texte de l’objet.|  
|IHF_NOSEPERATESUBJECT|La définition de cet indicateur signifie qu’il n’y a pas d’objet IntelliSense distinct. L’objet existe dans la mémoire tampon de contexte, par exemple dans le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> système IntelliSense traditionnel.|  
|IHF_SINGLELINESUBJECT|La définition de cet indicateur signifie que le sujet n’est pas capable d’être multiligne, par exemple dans une modification de ligne unique dans la fenêtre **Espion** .|  
|IHF_FORCECOMMITTOCONTEXT|Si cet indicateur est défini et que la mémoire tampon de contexte doit être mise à jour, l’hôte permet d’ignorer l’indicateur de lecture seule sur la mémoire tampon de contexte et de procéder à des modifications.|  
|IHF_OVERTYPE|La modification (dans l’objet ou le contexte) doit être effectuée en mode de Refrappe.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit et IVsIntellisenseHost. AfterCompletorCommit  
 Ces méthodes de rappel sont appelées par la fenêtre de saisie semi-automatique avant et après la validation du texte, pour permettre le prétraitement et le postérieur au traitement.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interface est une version co-créée de la fenêtre de saisie semi-automatique standard utilisée par l’environnement de développement intégré (IDE). Toute <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface peut rapidement implémenter IntelliSense à l’aide de cette interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop>

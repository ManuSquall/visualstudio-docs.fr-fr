---
title: Gestion des erreurs et des valeurs de retour | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 315315e925eecd45b1c001531f5ebb6be207b2e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306850"
---
# <a name="error-handling-and-return-values"></a>Gestion des erreurs et valeurs de retour
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages et COM utilisent la même architecture pour les erreurs. Le `SetErrorInfo` et `GetErrorInfo` fonctions font partie de l’interface de programmation d’application (API) Win32. Un VSPackage dans l’environnement de développement intégré (IDE) peut appeler ces global des API Win32 pour les informations d’erreur complètes enregistrement lors de la réception d’une notification d’erreur. Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fournit les assemblys PIA pour gérer les informations d’erreur.  
  
## <a name="interop-methods"></a>Méthodes d’interopérabilité  
 Pour des raisons pratiques, l’IDE fournit une méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, à utiliser au lieu d’appeler les API Win32. En code managé, utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Lorsqu’une erreur `HRESULT` arrive au niveau où le message d’erreur doit être affiché (il s’agit souvent de l’objet implémentant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Gestionnaire de commandes), l’IDE utilise une autre méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, pour afficher la boîte de message approprié. En code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (méthode).  
  
 En tant qu’un implémenteur de VSPackage, vos objets COM implémentent normalement `ISupportErrorInfo`. Le `ISupportErrorInfo` interface garantit que les informations d’erreur complètes peuvent déplacer verticalement de la chaîne d’appel. Les objets qui peuvent être utilisées dans les processus ou entre les threads doivent prendre en charge `ISupportErrorInfo` pour vous assurer que les informations d’erreur détaillée sont correctement marshalées vers l’appelant.  
  
 Tous les objets qui sont liées aux VSPackages et qui sont impliqués dans l’extension de l’IDE, notamment les fabriques d’éditeur, des éditeurs, des hiérarchies et proposé des services, doivent prendre en charge les informations d’erreur complètes. Bien que l’IDE ne nécessite pas ces objets VSPackage à implémenter `ISupportErrorInfo`, il est recommandé de toujours.  
  
 L’IDE est responsable de la consignation des informations sur les erreurs et de les afficher à un utilisateur de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] chaque fois qu’un `HRESULT` est propagé à l’IDE. L’IDE est également le mécanisme de création `ErrorInfo` objets.  
  
## <a name="general-guidelines"></a>Indications générales  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthodes pour définir et de signaler les erreurs qui sont internes à votre mise en œuvre VSPackage. Toutefois, en règle générale, suivez ces instructions pour la gestion des messages d’erreur dans votre VSPackage :  
  
-   Implémentez `ISupportErrorInfo` dans vos objets COM de VSPackage.  
  
-   Créer une erreur signalant le mécanisme qui appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode dans les objets qui implémentent <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Laisser l’IDE affiche les erreurs aux utilisateurs via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (méthode).  
  
## <a name="error-information-in-the-ide"></a>Informations d’erreur dans l’IDE  
 Les règles suivantes indiquent comment gérer les informations d’erreur dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE :  
  
-   Comme une stratégie pour garantir des informations sur l’erreur obsolète ne sont pas signalée aux utilisateurs, les fonctions qui appellent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthode doit tout d’abord appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode). Passez dans `null` pour effacer les messages d’erreur mis en cache avant l’appel de tout élément qui peut définir de nouvelles informations d’erreur.  
  
-   Les fonctions qui ne signalent pas directement les messages d’erreur sont uniquement autorisées à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode si qu’elles renvoient une erreur `HRESULT`. Il est permis d’effacer le `ErrorInfo` sur l’entrée à une fonction ou lors du retour <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La seule exception à cette règle est lorsqu’un appel retourne une erreur `HRESULT` à partir de laquelle le destinataire peut récupérer explicitement ou ignorer en toute sécurité.  
  
-   Toute partie qui ignore explicitement une erreur `HRESULT` doit appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode avec <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Sinon, le `ErrorInfo` objet peut être accidentellement utilisé lorsqu’une autre partie génère une erreur sans fournir leur propre `ErrorInfo`.  
  
-   Toutes les méthodes qui proviennent d’une erreur `HRESULT` est préférable d’appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode pour fournir des informations d’erreur complètes. Si le texte retourné `HRESULT` est spéciale `FACILITY_ITF` erreur, puis la méthode est nécessaire pour fournir un approprié `ErrorInfo`objet. Si l’erreur renvoyée est une erreur système standard (par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>et ainsi de suite.) il est acceptable de retourner le code d’erreur sans appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode). En tant qu’une stratégie de codage défensive, lorsqu’une erreur d’origine `HRESULT` (y compris les erreurs du système), appelez toujours le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode), soit avec `ErrorInfo` décrivant l’échec de plus en détail, ou `null`.  
  
-   Toutes les fonctions qui retournent une erreur d’origine par un autre appel doit transmettre les informations qui a été reçues de l’échec d’appellent le `HRESULT` sans modifier le `ErrorInfo` objet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automatisation des composants)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interface ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)


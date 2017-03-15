---
title: Gestion des erreurs et des valeurs de retour | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>Gestion des erreurs et des valeurs de retour
Les VSPackages et COM utilisent la même architecture pour les erreurs. Le `SetErrorInfo` et `GetErrorInfo` fonctions font partie de l’interface de programmation d’application (API) Win32. N’importe quel package VS dans l’environnement de développement intégré (IDE) peut appeler ces global des API Win32 pour enregistrer des informations erreur lors de la réception d’une notification d’erreur. Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit des assemblys PIA pour gérer les informations d’erreur.  
  
## <a name="interop-methods"></a>Méthodes d’interopérabilité  
 Pour des raisons pratiques, l’IDE fournit une méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, à utiliser au lieu d’appeler les API Win32.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> En code managé, utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Lorsqu’une erreur `HRESULT` arrive au niveau où le message d’erreur doit être affiché (il s’agit souvent de l’objet implémentant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Gestionnaire de commandes), l’IDE utilise une autre méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, pour afficher la boîte de message approprié.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> En code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 En tant qu’un implémenteur VSPackage, vos objets COM implémentent généralement `ISupportErrorInfo`. Le `ISupportErrorInfo` interface garantit que les informations d’erreur complètes peuvent déplacer verticalement jusqu'à la chaîne d’appel. Les objets qui peuvent être utilisées entre plusieurs processus ou entre plusieurs threads doivent prendre en charge `ISupportErrorInfo` pour vous assurer que les informations d’erreur complètes sont correctement marshalées vers l’appelant.  
  
 Tous les objets qui sont liées aux packages VS et qui sont impliqués dans l’extension de l’IDE, notamment les fabriques d’éditeur, des éditeurs, des hiérarchies et proposé des services, doivent prendre en charge les informations d’erreur complètes. Alors que l’IDE ne nécessite pas ces objets VSPackage implémenter `ISupportErrorInfo`, il est recommandé de toujours.  
  
 L’IDE est responsable des informations d’erreur de création de rapports et de les afficher à l’utilisateur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chaque fois qu’un `HRESULT` est propagé à l’IDE. L’IDE est également le mécanisme de création `ErrorInfo` objets.  
  
## <a name="general-guidelines"></a>Indications générales  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>méthodes pour définir et signaler les erreurs internes à votre mise en œuvre VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Toutefois, en règle générale, suivez ces instructions pour la gestion des messages d’erreur dans votre package VS :  
  
-   Implémentez `ISupportErrorInfo` dans les objets COM de VSPackage.  
  
-   Création d’un mécanisme qui appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode dans les objets qui implémentent <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> de signalement d’erreurs  
  
-   Permettent d’afficher les erreurs pour les utilisateurs via l’IDE les <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>Informations d’erreur dans l’IDE  
 Les règles suivantes indiquent comment gérer les informations d’erreur dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE :  
  
-   Comme une stratégie de défense afin de garantir qu’informations d’erreur obsolètes ne sont pas signalée aux utilisateurs, les fonctions qui appellent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>doit tout d’abord appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Transmettez `null` pour effacer les messages d’erreur mis en cache avant l’appel de tout élément qui peut définir de nouvelles informations d’erreur.  
  
-   Les fonctions qui ne signalent pas directement les messages d’erreur sont uniquement autorisées à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode si qu’elles renvoient une erreur `HRESULT`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Il est permis d’effacer le `ErrorInfo` sur l’entrée à une fonction ou lors du retour <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> La seule exception à cette règle est lorsqu’un appel retourne une erreur `HRESULT` à partir de la partie réceptrice peut récupérer explicitement ou ignorer en toute sécurité.  
  
-   Toute partie qui ignore explicitement une erreur `HRESULT` doit appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Dans le cas contraire, le `ErrorInfo` objet peut être utilisé par inadvertance lorsqu’une autre partie génère une erreur sans fournir leur propre `ErrorInfo`.  
  
-   Toutes les méthodes qui proviennent d’une erreur `HRESULT` sont invités à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode pour fournir des informations d’erreur complètes.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Si retourné `HRESULT` est spéciale `FACILITY_ITF` erreur, puis la méthode est requise pour fournir une propres `ErrorInfo`objet. Si l’erreur renvoyée est une erreur système standard (par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>et ainsi de suite.) il vaut mieux renvoyer le code d’erreur sans appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> Une stratégie de codage défensif, lorsqu’une erreur d’origine `HRESULT` (y compris les erreurs de système), appelez toujours la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>(méthode), soit avec `ErrorInfo` décrivant l’échec en détail, ou `null`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   Toutes les fonctions qui retournent une erreur émises par un autre appel doit passer des informations a été reçues de l’échec d’appellent le `HRESULT` sans modifier le `ErrorInfo` objet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (composant Automation)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interface ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)

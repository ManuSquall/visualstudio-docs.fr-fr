---
title: Gestion des erreurs et des valeurs de retour | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cfbeef2de041cfd71fbf163d7860d903a6cb59e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135499"
---
# <a name="error-handling-and-return-values"></a>Gestion des erreurs et des valeurs de retour
VSPackages et COM utilisent la même architecture pour les erreurs. Le `SetErrorInfo` et `GetErrorInfo` fonctions font partie de l’interface de programmation d’application (API) Win32. Un VSPackage dans l’environnement de développement intégré (IDE) peut appeler ces global des API Win32 pour les informations d’erreur complètes enregistrement lors de la réception d’une notification d’erreur. Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit les assemblys PIA pour gérer les informations d’erreur.  
  
## <a name="interop-methods"></a>Méthodes d’interopérabilité  
 Pour des raisons pratiques, l’IDE fournit une méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, à utiliser au lieu d’appeler les API Win32. En code managé, utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Lorsqu’une erreur `HRESULT` arrive au niveau où le message d’erreur doit être affiché (il s’agit souvent de l’objet implémentant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> le Gestionnaire de commandes), l’IDE utilise une autre méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, pour afficher la boîte de message approprié. En code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (méthode).  
  
 En tant qu’un responsable de l’implémentation VSPackage, vos objets COM implémentent normalement `ISupportErrorInfo`. Le `ISupportErrorInfo` interface garantit que les informations d’erreur complètes peuvent déplacer verticalement haut de la chaîne d’appel. Les objets qui peuvent être utilisées dans les processus ou entre plusieurs threads doivent prendre en charge `ISupportErrorInfo` pour vous assurer que les informations d’erreur détaillée sont correctement marshalées vers l’appelant.  
  
 Tous les objets qui sont liés aux packages VS, et qui sont impliquées dans l’extension de l’IDE, y compris les fabriques d’éditeur, des éditeurs, des hiérarchies et proposé des services, doivent prendre en charge les informations d’erreur complètes. Bien que l’IDE ne nécessite pas ces objets VSPackage à implémenter `ISupportErrorInfo`, il est recommandé de toujours.  
  
 L’IDE est responsable des informations sur l’erreur de création de rapports et de les afficher à l’utilisateur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chaque fois qu’un `HRESULT` est propagé à l’IDE. L’IDE est également le mécanisme de création `ErrorInfo` objets.  
  
## <a name="general-guidelines"></a>Indications générales  
 Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthodes pour définir et de signaler les erreurs qui sont internes à votre implémentation du VSPackage. Toutefois, en règle générale, suivez ces instructions pour la gestion des messages d’erreur dans votre package Visual Studio :  
  
-   Implémentez `ISupportErrorInfo` dans vos objets COM du VSPackage.  
  
-   Créer une erreur signalant le mécanisme qui appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode dans les objets qui implémentent <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Laisser l’IDE affiche les erreurs pour les utilisateurs via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (méthode).  
  
## <a name="error-information-in-the-ide"></a>Informations d’erreur dans l’IDE  
 Les règles suivantes indiquent comment gérer les informations d’erreur dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE :  
  
-   Comme une stratégie de protection afin de garantir qu’informations d’erreur obsolètes ne sont pas signalée aux utilisateurs, les fonctions qui appellent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> doit tout d’abord appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode). Passez dans `null` pour effacer les messages d’erreur mis en cache avant l’appel de tout élément qui peut définir de nouvelles informations d’erreur.  
  
-   Les fonctions qui ne signalent pas directement les messages d’erreur sont uniquement autorisées à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode si qu’elles renvoient une erreur `HRESULT`. Il est possible d’effacer le `ErrorInfo` sur l’entrée à une fonction ou lors du retour <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La seule exception à cette règle est lorsqu’un appel retourne une erreur `HRESULT` à partir de laquelle le destinataire peut explicitement récupérer ou ignorer en toute sécurité.  
  
-   N’importe quelle partie explicitement ignore une erreur `HRESULT` doit appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode avec <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Dans le cas contraire, le `ErrorInfo` objet peut être utilisé par inadvertance lorsqu’une autre partie génère une erreur sans fournir leur propre `ErrorInfo`.  
  
-   Toutes les méthodes qui proviennent d’une erreur `HRESULT` sont encouragés à appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode pour fournir des informations d’erreur complètes. Si retourné `HRESULT` est spéciale `FACILITY_ITF` des erreurs, puis la méthode est requise pour fournir un propres `ErrorInfo`objet. Si l’erreur retournée est une erreur système standard (par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>et ainsi de suite) il est acceptable pour retourner le code d’erreur sans appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode). Une stratégie de codage défensif, lorsqu’une erreur d’origine `HRESULT` (y compris les erreurs de système), appelez toujours la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (méthode), soit avec `ErrorInfo` décrivant l’échec de manière plus détaillée, ou `null`.  
  
-   Toutes les fonctions qui retournent une erreur d’origine par un autre appel doit passer des informations qui a été reçues de l’échec d’appellent le `HRESULT` sans modifier le `ErrorInfo` objet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (composant Automation)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interface ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
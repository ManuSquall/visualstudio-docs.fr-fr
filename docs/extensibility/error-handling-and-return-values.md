---
title: Valeurs de traitement et de rendement des erreurs (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711936"
---
# <a name="error-handling-and-return-values"></a>Valeurs de traitement et de retour d’erreurs
VSPackages et COM utilisent la même architecture pour les erreurs. Les `SetErrorInfo` `GetErrorInfo` fonctions et les fonctions font partie de l’interface de programmation d’applications Win32 (API). Tout VSPackage dans l’environnement de développement intégré (IDE) peut appeler ces API Win32 globales pour enregistrer de riches informations d’erreur lors de la réception d’une notification d’erreur. Le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit des assemblages interop pour gérer les informations d’erreur.

## <a name="interop-methods"></a>Méthodes Interop
 Comme commodité, l’IDE fournit <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>une méthode, à utiliser au lieu d’appeler les API Win32. Dans l’utilisation <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>du code géré . Lorsqu’une `HRESULT` erreur arrive au niveau où le message d’erreur <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> doit être affiché (c’est <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>souvent l’objet implémentant un gestionnaire de commande), l’IDE utilise une autre méthode, pour afficher la boîte de message appropriée. Dans le code <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> géré utiliser la méthode.

 En tant qu’implémentateur VSPackage, vos objets COM implémentent `ISupportErrorInfo`normalement . L’interface `ISupportErrorInfo` garantit que les informations d’erreur riches peuvent se déplacer verticalement vers le haut de la chaîne d’appel. Les objets qui peuvent être utilisés entre `ISupportErrorInfo` les processus ou à travers les threads doivent prendre en charge pour s’assurer que les informations d’erreur riches sont correctement marshaled de nouveau à l’appelant.

 Tous les objets qui sont liés à VSPackages et qui sont impliqués dans l’extension de l’IDE, y compris les usines de rédaction, les éditeurs, les hiérarchies, et les services offerts, devraient soutenir de riches informations d’erreur. Bien que l’IDE n’exige pas `ISupportErrorInfo`ces objets VSPackage pour implémenter , il est toujours encouragé.

 L’IDE est responsable de signaler les informations [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] d’erreur et de les afficher à un utilisateur de chaque fois qu’un `HRESULT` est propagé à l’IDE. L’IDE est également `ErrorInfo` le mécanisme de création d’objets.

## <a name="general-guidelines"></a>Recommandations générales
 Vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> les méthodes et les méthodes pour définir et signaler les erreurs internes à votre implémentation VSPackage ainsi. Toutefois, en règle générale, suivez ces lignes directrices pour le traitement des messages d’erreur dans votre VSPackage :

- Implémentez `ISupportErrorInfo` vos objets VSPackage COM.

- Créez un mécanisme de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> déclaration d’erreurs <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>qui appelle la méthode dans les objets qui implémentent .

- Laissez les erreurs d’affichage <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> IDE aux utilisateurs à travers la méthode.

## <a name="error-information-in-the-ide"></a>Informations d’erreur dans l’IDE
 Les règles suivantes indiquent comment traiter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] les informations d’erreur dans l’IDE :

- En tant que stratégie défensive pour garantir que les informations d’erreur périmées ne sont pas signalées aux utilisateurs, les fonctions qui appellent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthode doivent d’abord appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode. Passez pour `null` effacer les messages d’erreur mis en cache avant d’appeler tout ce qui pourrait définir de nouvelles informations d’erreur.

- Les fonctions qui ne signalent pas directement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> les messages d’erreur ne sont autorisées à appeler la méthode que s’ils renvoient une erreur `HRESULT`. Il est permis d’effacer l’entrée `ErrorInfo` d’une fonction ou lors du retour <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La seule exception à cette règle est `HRESULT` lorsqu’un appel renvoie une erreur à partir de laquelle la partie bénéficiaire peut explicitement récupérer ou ignorer en toute sécurité.

- Toute partie qui ignore `HRESULT` explicitement une <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> erreur <xref:Microsoft.VisualStudio.VSConstants.S_OK>doit appeler la méthode avec . Sinon, `ErrorInfo` l’objet peut être accidentellement utilisé quand une `ErrorInfo`autre partie génère une erreur sans fournir leur propre .

- Toutes les méthodes qui `HRESULT` sont à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> l’origine d’une erreur sont encouragées à appeler la méthode pour fournir des informations d’erreur riches. Si le `HRESULT` retour `FACILITY_ITF` est une erreur spéciale, alors `ErrorInfo`la méthode est nécessaire pour fournir un objet approprié. Si l’erreur retournée est une erreur <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>système <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>standard (par exemple, , , , , et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ainsi de suite.) il est acceptable de retourner le code d’erreur sans appeler explicitement la méthode. Comme stratégie de codage défensif, `HRESULT` lors de l’origine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> d’une `ErrorInfo` erreur (y compris les `null`erreurs du système), toujours appeler la méthode, soit avec la description de l’échec plus en détail, ou .

- Toutes les fonctions qui renvoient une erreur résultant d’un autre appel `HRESULT` doivent transmettre `ErrorInfo` les informations reçues de l’appel défaillant dans l’objet sans modifier l’objet.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automatisation des composants)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)

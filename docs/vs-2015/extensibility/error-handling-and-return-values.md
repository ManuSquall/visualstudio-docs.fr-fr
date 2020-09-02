---
title: Gestion des erreurs et valeurs de retour | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696330"
---
# <a name="error-handling-and-return-values"></a>Gestion des erreurs et valeurs de retour
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les VSPackages et COM utilisent la même architecture pour les erreurs. Les `SetErrorInfo` `GetErrorInfo` fonctions et font partie de l’interface de programmation d’applications (API) Win32. Tout VSPackage dans l’environnement de développement intégré (IDE) peut appeler ces API Win32 globales pour enregistrer des informations d’erreur complètes lors de la réception d’une notification d’erreur. [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Fournit des assemblys d’interopérabilité pour gérer les informations d’erreur.  
  
## <a name="interop-methods"></a>Méthodes d’interopérabilité  
 Pour plus de commodité, l’IDE fournit une méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , à utiliser au lieu d’appeler les API Win32. En code managé, utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Lorsqu’une erreur se produit `HRESULT` au niveau de l’affichage du message d’erreur (il s’agit souvent de l’objet qui implémente un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Gestionnaire de commandes), l’IDE utilise une autre méthode, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , pour afficher la boîte de message appropriée. En code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthode.  
  
 En tant qu’implémenteur VSPackage, vos objets COM implémentent normalement `ISupportErrorInfo` . L' `ISupportErrorInfo` interface garantit que les informations d’erreur enrichies peuvent se déplacer verticalement vers le haut de la chaîne d’appel. Les objets qui peuvent être utilisés entre les processus ou entre les threads doivent prendre en charge `ISupportErrorInfo` pour s’assurer que les informations d’erreur enrichies sont correctement remarshalées vers l’appelant.  
  
 Tous les objets liés aux VSPackages et qui sont impliqués dans l’extension de l’IDE, y compris les fabriques d’éditeur, les éditeurs, les hiérarchies et les services proposés, doivent prendre en charge des informations d’erreur enrichies. Bien que l’IDE ne nécessite pas l’implémentation de ces objets VSPackage `ISupportErrorInfo` , il est toujours recommandé.  
  
 L’IDE est chargé de signaler les informations d’erreur et de les afficher à un utilisateur de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] chaque fois qu’un `HRESULT` est propagé à l’IDE. L’IDE est également le mécanisme de création d' `ErrorInfo` objets.  
  
## <a name="general-guidelines"></a>Instructions générales  
 Vous pouvez utiliser les <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthodes et pour définir et signaler également les erreurs internes à votre implémentation de VSPackage. Toutefois, en règle générale, suivez ces instructions pour gérer les messages d’erreur dans votre VSPackage :  
  
- Implémentez `ISupportErrorInfo` dans vos objets com VSPackage.  
  
- Créez un mécanisme de création de rapports d’erreurs qui appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode dans des objets qui implémentent <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- Laissez l’IDE afficher les erreurs aux utilisateurs par le biais de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthode.  
  
## <a name="error-information-in-the-ide"></a>Informations d’erreur dans l’IDE  
 Les règles suivantes indiquent comment gérer les informations d’erreur dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE :  
  
- En guise de stratégie défensive pour garantir que les informations d’erreur périmées ne sont pas signalées aux utilisateurs, les fonctions qui appellent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> méthode doivent d’abord appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode. Transmettez `null` pour effacer les messages d’erreur mis en cache avant d’appeler tout ce qui peut définir de nouvelles informations sur l’erreur.  
  
- Les fonctions qui ne signalent pas directement les messages d’erreur sont autorisées à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode uniquement si elles retournent une erreur `HRESULT` . Il est permis d’effacer le `ErrorInfo` sur l’entrée d’une fonction ou de retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> . La seule exception à cette règle est lorsqu’un appel retourne une erreur `HRESULT` à partir de laquelle le tiers récepteur peut récupérer explicitement ou ignorer en toute sécurité.  
  
- Tout tiers qui ignore explicitement une erreur `HRESULT` doit appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode avec <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Dans le cas contraire, l' `ErrorInfo` objet peut être utilisé par inadvertance lorsqu’un autre tiers génère une erreur sans fournir leur propre `ErrorInfo` .  
  
- Toutes les méthodes qui proviennent d’une erreur `HRESULT` sont encouragées à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode pour fournir des informations détaillées sur l’erreur. Si le retourné `HRESULT` est une `FACILITY_ITF` erreur spéciale, la méthode est requise pour fournir un objet approprié `ErrorInfo` . Si l’erreur renvoyée est une erreur système standard (par exemple,,,,, etc <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> .), il est acceptable de retourner le code d’erreur sans appeler explicitement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode. En tant que stratégie de codage défensive, lors de l’origine d’une erreur `HRESULT` (y compris les erreurs système), appelez toujours la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> méthode, soit en `ErrorInfo` décrivant la défaillance de manière plus détaillée, soit `null` .  
  
- Toutes les fonctions qui retournent une erreur provenant d’un autre appel doivent transmettre les informations reçues de l’appel ayant échoué dans le `HRESULT` sans modifier l' `ErrorInfo` objet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automatisation des composants)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo, interface](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)

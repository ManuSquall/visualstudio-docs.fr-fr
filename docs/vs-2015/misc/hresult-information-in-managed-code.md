---
title: Informations HRESULT dans du Code managé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 53ff7b49414e3473c74a41008f381bb207e45fd0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414676"
---
# <a name="hresult-information-in-managed-code"></a>Informations HRESULT dans du Code managé
L’interaction entre le code managé et COM peut entraîner des problèmes quand vous rencontrez des valeurs de retour HRESULT.  
  
 Dans une interface COM, une valeur de retour HRESULT peut jouer ces rôles :  
  
- Fournir des informations d’erreur (par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
- Fournir des informations d’état sur le comportement normal du programme.  
  
  Quand COM appelle du code managé, les HRESULT peuvent entraîner ces problèmes :  
  
- Les fonctions COM qui retournent des valeurs HRESULT inférieures à zéro (codes d’échec) génèrent des exceptions.  
  
- Les méthodes COM qui retournent régulièrement deux codes de réussite différents ou plus, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, ne peuvent pas être distinguées.  
  
  Étant donné qu’un grand nombre des fonctions COM [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] retournent des valeurs HRESULT inférieures à zéro ou des codes de réussite différents, les assemblys d’interopérabilité [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ont été écrits de sorte que les signatures de méthode soient conservées. Toutes les méthodes d’interopérabilité [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] sont de type `int` . Des valeurs HRESULT sont transmises via la couche d’interopérabilité sans modification et sans générer d’exceptions.  
  
  Étant donné qu’une fonction COM retourne un HRESULT à la méthode managée qui l’appelle, la méthode qui appelle doit vérifier le HRESULT et lever des exceptions si nécessaire.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestion des HRESULT retournés au code managé à partir de COM  
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contient la méthode <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> qui lève une exception COM, selon la valeur HRESULT qui lui est passée.  
  
 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lève une exception dès lors qu’elle est passée à un HRESULT qui a une valeur inférieure à zéro. Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et quand aucune exception ne doit être levée, les valeurs des HRESULT supplémentaires doivent être passées à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> une fois les valeurs testées. Si la valeur HRESULT testée correspond à une valeur HRESULT explicitement passée à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.  
  
> [!NOTE]
> Le <xref:Microsoft.VisualStudio.VSConstants> classe contient des constantes pour les valeurs HRESULT courantes, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK> et <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, et [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULT, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> fournit également les méthodes <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> et <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> qui correspondent aux macros SUCCEEDED et FAILED dans COM.  
  
 Par exemple, considérez l’appel de fonction suivant, dans lequel <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> est une valeur de retour acceptable, alors que les autres valeurs HRESULT inférieures à zéro représentent une erreur.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 S’il existe plusieurs valeurs de retour acceptables, les autres valeurs HRESULT peuvent être simplement ajoutées à la liste dans l’appel à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Retour de valeurs HRESULT à COM à partir de code managé  
 Si aucune exception ne se produit, le code managé retourne <xref:Microsoft.VisualStudio.VSConstants.S_OK> à la fonction COM qui l’a appelé. COM interop prend en charge les exceptions courantes qui sont fortement typées dans du code managé. Par exemple, une méthode qui reçoit un argument `null` inacceptable lève une <xref:System.ArgumentNullException>.  
  
 Si vous ne savez pas quelle exception lever, alors que vous connaissez la valeur HRESULT à retourner à COM, vous pouvez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pour lever une exception appropriée. Cela fonctionne même avec une erreur non standard, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> essaie de mapper la valeur HRESULT qui lui est passée sur une exception fortement typée. Si ce n’est pas possible, une exception COM générique est levée. Le résultat final est que la valeur HRESULT que vous passez à <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> à partir du code managé est retournée à la fonction COM qui l’a appelée.  
  
> [!NOTE]
> Les exceptions nuisent aux performances et ont vocation à indiquer des conditions anormales pour le programme. Les conditions qui se produisent souvent doivent être gérées instantanément, au lieu de lever une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages gérés](../misc/managed-vspackages.md)   
 [Interopération avec du code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Guide pratique pour Map HRESULTs and Exceptions](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Génération de composants COM pour l’interopérabilité](http://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages gérés](../misc/managed-vspackages.md)
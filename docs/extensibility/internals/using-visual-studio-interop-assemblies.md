---
title: Utilisation des assemblys d’interopérabilité Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704130"
---
# <a name="using-visual-studio-interop-assemblies"></a>Utilisation des assemblys d’interopérabilité de Visual Studio
Les assemblys d’interopérabilité Visual Studio permettent aux applications managées d’accéder aux interfaces COM qui fournissent l’extensibilité Visual Studio. Il existe des différences entre les interfaces COM simples et leurs versions d’interopérabilité. Par exemple, les valeurs HRESULT sont généralement représentées en tant que valeurs int et doivent être gérées de la même façon que les exceptions, et les paramètres (surtout les paramètres out) sont traités différemment.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestion des HRESULT retournés au code managé à partir de COM
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contient la méthode <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> qui lève une exception COM, selon la valeur HRESULT qui lui est passée.

 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lève une exception dès lors qu’elle est passée à un HRESULT qui a une valeur inférieure à zéro. Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et quand aucune exception ne doit être levée, les valeurs des HRESULT supplémentaires doivent être passées à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> une fois les valeurs testées. Si la valeur HRESULT testée correspond à une valeur HRESULT explicitement passée à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> classe contient des constantes pour les valeurs HRESULT courantes, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK> et <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , et les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valeurs HRESULT, par exemple <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> fournit également les méthodes <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> et <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> qui correspondent aux macros SUCCEEDED et FAILED dans COM.

 Par exemple, considérez l’appel de fonction suivant, dans lequel <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> est une valeur de retour acceptable, alors que les autres valeurs HRESULT inférieures à zéro représentent une erreur.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 S’il existe plusieurs valeurs de retour acceptables, les autres valeurs HRESULT peuvent être simplement ajoutées à la liste dans l’appel à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Retour de valeurs HRESULT à COM à partir de code managé
 Si aucune exception ne se produit, le code managé retourne <xref:Microsoft.VisualStudio.VSConstants.S_OK> à la fonction COM qui l’a appelé. COM interop prend en charge les exceptions courantes qui sont fortement typées dans du code managé. Par exemple, une méthode qui reçoit un argument `null` inacceptable lève une <xref:System.ArgumentNullException>.

 Si vous ne savez pas quelle exception lever, alors que vous connaissez la valeur HRESULT à retourner à COM, vous pouvez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pour lever une exception appropriée. Cela fonctionne même avec une erreur non standard, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> essaie de mapper la valeur HRESULT qui lui est passée sur une exception fortement typée. Si ce n’est pas possible, une exception COM générique est levée. Le résultat final est que la valeur HRESULT que vous passez à <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> à partir du code managé est retournée à la fonction COM qui l’a appelée.

> [!NOTE]
> Les exceptions nuisent aux performances et ont vocation à indiquer des conditions anormales pour le programme. Les conditions qui se produisent souvent doivent être gérées instantanément, au lieu de lever une exception.

## <a name="iunknown-parameters-passed-as-type-void"></a>Paramètres IUnknown passés comme type void * *
 Recherchez les paramètres [out] définis en tant que type `void **` dans l’interface com, mais qui sont définis comme `[``iid_is``]` dans le prototype de la méthode de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité.

 Parfois, une interface COM génère un `IUnknown` objet, et l’interface com la passe en tant que type `void **` . Ces interfaces sont particulièrement importantes, car si la variable est définie sur [out] dans le IDL, l' `IUnknown` objet est compté par référence à l’aide de la `AddRef` méthode. Une fuite de mémoire se produit si l’objet n’est pas géré correctement.

> [!NOTE]
> Un `IUnknown` objet créé par l’interface com et retourné dans une variable [out] provoque une fuite de mémoire s’il n’est pas explicitement libéré.

 Les méthodes managées qui gèrent ces objets doivent traiter <xref:System.IntPtr> comme un pointeur vers un `IUnknown` objet et appeler la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> méthode pour obtenir l’objet. L’appelant doit ensuite effectuer un cast de la valeur de retour vers le type approprié. Lorsque l’objet n’est plus nécessaire, appelez <xref:System.Runtime.InteropServices.Marshal.Release%2A> pour le libérer.

 Voici un exemple d’appel de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> méthode et de gestion `IUnknown` correcte de l’objet :

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> Les méthodes suivantes sont connues pour passer des `IUnknown` pointeurs d’objet en tant que type <xref:System.IntPtr> . Gérez-les comme décrit dans cette section.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Paramètres facultatifs [out]
 Recherchez les paramètres définis en tant que type de données [out] ( `int` , `object` , etc.) dans l’interface com, mais qui sont définis en tant que tableaux du même type de données dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.

 Certaines interfaces COM, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , traitent les paramètres [out] comme facultatifs. Si un objet n’est pas requis, ces interfaces COM retournent un `null` pointeur comme valeur de ce paramètre au lieu de créer l’objet [out]. C'est la procédure normale. Pour ces interfaces, les `null` pointeurs sont considérés comme faisant partie du comportement correct du VSPackage et aucune erreur n’est retournée.

 Étant donné que le CLR n’autorise pas la valeur d’un paramètre [out] `null` , une partie du comportement conçu de ces interfaces n’est pas directement disponible dans le code managé. Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes d’assembly d’interopérabilité pour les interfaces affectées contournent le problème en définissant les paramètres appropriés en tant que tableaux, car le CLR autorise le passage de `null` tableaux.

 Les implémentations managées de ces méthodes doivent placer un `null` tableau dans le paramètre lorsqu’il n’y a rien à retourner. Sinon, créez un tableau d’un élément du type correct et placez la valeur de retour dans le tableau.

 Les méthodes managées qui reçoivent des informations à partir d’interfaces avec des paramètres facultatifs [out] reçoivent le paramètre sous la forme d’un tableau. Examinez simplement la valeur du premier élément du tableau. Si ce n’est pas le cas `null` , traite le premier élément comme s’il s’agissait du paramètre d’origine.

## <a name="passing-constants-in-pointer-parameters"></a>Passage de constantes dans des paramètres de pointeur
 Recherchez les paramètres définis en tant que pointeurs [in] dans l’interface COM, mais qui sont définis en tant que <xref:System.IntPtr> type dans le prototype de méthode de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité.

 Un problème similaire se produit lorsqu’une interface COM passe une valeur spéciale, telle que 0,-1 ou-2, au lieu d’un pointeur d’objet. Contrairement [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] à, le CLR n’autorise pas le cast des constantes en tant qu’objets. Au lieu de cela, l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité définit le paramètre en tant que <xref:System.IntPtr> type.

 Les implémentations managées de ces méthodes doivent tirer parti du fait que la <xref:System.IntPtr> classe a `int` des `void *` constructeurs et pour créer un <xref:System.IntPtr> à partir d’un objet ou d’une constante entière, le cas échéant.

 Les méthodes managées qui reçoivent <xref:System.IntPtr> des paramètres de ce type doivent utiliser les <xref:System.IntPtr> opérateurs de conversion de type pour gérer les résultats. Tout d’abord, convertissez le <xref:System.IntPtr> en `int` et testez-le par rapport aux constantes entières appropriées. Si aucune valeur ne correspond, convertissez-la en un objet du type requis et continuez.

 Pour obtenir des exemples, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valeurs de retour OLE passées en tant que paramètres [out]
 Recherchez les méthodes qui ont une `retval` valeur de retour dans l’interface com, mais qui ont une `int` valeur de retour et un paramètre de tableau [out] supplémentaire dans le prototype de méthode de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité. Il doit être clair que ces méthodes nécessitent un traitement spécial, car les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypes de méthode de l’assembly d’interopérabilité ont un paramètre de plus que les méthodes de l’interface com.

 De nombreuses interfaces COM qui gèrent l’activité OLE envoient des informations sur l’État OLE au programme appelant stocké dans la `retval` valeur de retour de l’interface. Au lieu d’utiliser une valeur de retour, les méthodes de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité correspondant renvoient les informations au programme appelant stocké dans un paramètre de tableau [out].

 Les implémentations managées de ces méthodes doivent créer un tableau à un seul élément du même type que le paramètre [out] et les placer dans le paramètre. La valeur de l’élément de tableau doit être la même que le COM approprié `retval` .

 Les méthodes managées qui appellent des interfaces de ce type doivent extraire le premier élément du tableau [out]. Cet élément peut être traité comme s’il s’agissait `retval` d’une valeur de retour de l’interface com correspondante.

## <a name="see-also"></a>Voir aussi
- [Interopération avec du code non managé](/dotnet/framework/interop/index)

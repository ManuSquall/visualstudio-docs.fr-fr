---
title: À l’aide des assemblys d’interopérabilité Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfc7c2d65ddf53121c10e1986cd774744f703028
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324545"
---
# <a name="using-visual-studio-interop-assemblies"></a>Utilisation des assemblys d’interopérabilité de Visual Studio
Les assemblys d’interopérabilité Visual Studio permettent aux applications gérées accéder aux interfaces COM qui offrent une extensibilité de Visual Studio. Il existe quelques différences entre les interfaces COM droites et leurs versions interop. Par exemple, les valeurs HRESULT sont généralement représentées sous forme de valeurs de type int et doivent être gérées de la même façon que les exceptions, et paramètres (en particulier les paramètres de sortie) sont traités différemment.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestion des HRESULT retournés au code managé à partir de COM
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contient la méthode <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> qui lève une exception COM, selon la valeur HRESULT qui lui est passée.

 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lève une exception dès lors qu’elle est passée à un HRESULT qui a une valeur inférieure à zéro. Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et quand aucune exception ne doit être levée, les valeurs des HRESULT supplémentaires doivent être passées à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> une fois les valeurs testées. Si la valeur HRESULT testée correspond à une valeur HRESULT explicitement passée à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.

> [!NOTE]
> Le <xref:Microsoft.VisualStudio.VSConstants> classe contient des constantes pour les valeurs HRESULT courantes, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK> et <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> fournit également les méthodes <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> et <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> qui correspondent aux macros SUCCEEDED et FAILED dans COM.

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

## <a name="iunknown-parameters-passed-as-type-void"></a>Paramètres de IUnknown passés en tant que Type void **
 Recherchez les [paramètres qui sont définis en tant que type out] `void **` dans le modèle COM interface, mais qui sont définis comme `[``iid_is``]` dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.

 Parfois, une interface COM génère une `IUnknown` objet et l’interface COM puis passe en tant que type `void **`. Ces interfaces sont particulièrement importants, car si la variable est définie en tant que [out] dans le fichier IDL, puis le `IUnknown` objet est comptée par référence avec le `AddRef` (méthode). Une fuite de mémoire se produit si l’objet n’est pas gérée correctement.

> [!NOTE]
> Un `IUnknown` objet créé par l’interface COM et retourné dans une variable [out] entraîne une fuite de mémoire si elle n’est pas explicitement libéré.

 Les méthodes managées qui gèrent ces objets doivent considérer <xref:System.IntPtr> comme un pointeur vers un `IUnknown` et appelez le <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> méthode pour obtenir l’objet. L’appelant doit alors convertir la valeur de retour pour le type est approprié. Lorsque l’objet n’est plus nécessaire, appelez <xref:System.Runtime.InteropServices.Marshal.Release%2A> à le libérer.

 Voici un exemple d’appel la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> (méthode) et la gestion de la `IUnknown` objet correctement :

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
> Les méthodes suivantes sont connus pour passer `IUnknown` des pointeurs d’objet en tant que type <xref:System.IntPtr>. Les gérer comme décrit dans cette section.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Facultatif de [paramètres out]
 Recherchez les paramètres qui sont définis en tant que [out] type de données (`int`, `object`, et ainsi de suite) dans le modèle COM interface, mais qui sont définis en tant que tableaux du même type de données dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.

 Certains COM des interfaces, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, traiter les [paramètres comme étant facultatifs out]. Si un objet n’est pas requis, le retour de ces interfaces COM une `null` pointeur en tant que la valeur de ce paramètre au lieu de créer l’objet [out]. Ceci est normal. Pour ces interfaces, `null` pointeurs sont supposées en tant que partie du comportement correct du VSPackage, et aucune erreur n’est retournée.

 Étant donné que le CLR n’autorise pas la valeur de paramètre [out] pour être `null`, partie du comportement de ces interfaces conçu n’est pas directement disponible dans du code géré. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes d’assembly d’interopérabilité pour les interfaces affectés contournent le problème en définissant les paramètres pertinents en tant que tableaux, car le CLR permet la transmission de `null` tableaux.

 Les implémentations managées de ces méthodes doivent placer un `null` tableau dans le paramètre quand il n’y a rien à retourner. Sinon, créez un tableau d’un élément du type correct et placer la valeur de retour dans le tableau.

 Gérés des méthodes qui reçoivent des informations à partir d’interfaces avec facultatif [out] Paramètres reçoivent le paramètre sous forme de tableau. Il suffit d’examiner la valeur du premier élément du tableau. Si ce n’est pas `null`, traiter le premier élément comme s’il était le paramètre d’origine.

## <a name="passing-constants-in-pointer-parameters"></a>Constantes de passage de paramètres de pointeur
 Recherchez les paramètres qui sont définies comme [in] pointeurs dans l’interface COM, mais qui sont définies comme un <xref:System.IntPtr> tapez dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.

 Un problème similaire se produit lorsqu’une interface COM transmet une valeur spéciale, telles que 0, -1 ou -2, au lieu d’un pointeur d’objet. Contrairement à [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], le CLR n’autorise pas les constantes à être casté en tant qu’objets. Au lieu de cela, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly d’interopérabilité définit le paramètre comme un <xref:System.IntPtr> type.

 Des implémentations managées de ces méthodes doivent tirer parti du fait que le <xref:System.IntPtr> classe dispose à la fois `int` et `void *` constructeurs pour créer un <xref:System.IntPtr> à partir d’un objet ou une constante entière, comme il convient.

 Gérés des méthodes qui reçoivent <xref:System.IntPtr> paramètres de ce type doivent utiliser le <xref:System.IntPtr> des opérateurs de conversion pour gérer les résultats de type. Tout d’abord convertir le <xref:System.IntPtr> à `int` et testez-le par rapport à des constantes entières pertinentes. Si aucune valeur ne correspondre, la convertir en un objet du type requis et continuer.

 Pour des exemples, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE retourner valeurs passées comme [paramètre out]
 Recherchez les méthodes qui ont un `retval` valeur de retour dans l’interface COM, mais qui ont un `int` valeur de retour et un autre [paramètre de tableau dans out] le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité. Il doit être clair que ces méthodes nécessitent une gestion spéciale, car le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypes de méthode d’assembly d’interopérabilité ont un paramètre supplémentaire que les méthodes d’interface COM.

 Nombre d’interfaces COM qui traitent de l’activité OLE envoyer des informations sur l’état OLE revenir au programme appelant stocké dans le `retval` retourner la valeur de l’interface. Au lieu d’utiliser une valeur de retour correspondants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes de l’assembly d’interopérabilité envoient les informations au programme appelant stocké dans un paramètre [out] paramètre de tableau.

 Les implémentations managées de ces méthodes doivent créer un seul élément tableau du même type que le paramètre [out] et le placer dans le paramètre. La valeur de l’élément de tableau doit être le même que le modèle COM approprié `retval`.

 Les méthodes managées qui appellent les interfaces de ce type doivent extraire le premier élément hors du tableau [out]. Cet élément peut être traité comme s’il s’agissait d’un `retval` valeur de retour à partir de l’interface COM correspondante.

## <a name="see-also"></a>Voir aussi
- [Interopération avec du code non managé](/dotnet/framework/interop/index)
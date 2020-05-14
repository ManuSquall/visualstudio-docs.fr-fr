---
title: Utilisation des assemblages Interop Visual Studio (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704130"
---
# <a name="using-visual-studio-interop-assemblies"></a>Utilisation des assemblys d’interopérabilité de Visual Studio
Les assemblages interop Visual Studio permettent aux applications gérées d’accéder aux interfaces COM qui fournissent l’extensibility Visual Studio. Il existe quelques différences entre les interfaces COM droites et leurs versions interop. Par exemple, les HRESULT sont généralement représentés comme des valeurs int et doivent être traités de la même manière que les exceptions, et les paramètres (en particulier les paramètres) sont traités différemment.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestion des HRESULT retournés au code managé à partir de COM
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contient la méthode <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> qui lève une exception COM, selon la valeur HRESULT qui lui est passée.

 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lève une exception dès lors qu’elle est passée à un HRESULT qui a une valeur inférieure à zéro. Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et quand aucune exception ne doit être levée, les valeurs des HRESULT supplémentaires doivent être passées à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> une fois les valeurs testées. Si la valeur HRESULT testée correspond à une valeur HRESULT explicitement passée à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> classe contient des constantes pour les <xref:Microsoft.VisualStudio.VSConstants.S_OK> HRESULTS communs, par exemple, <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>et , et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> fournit également les méthodes <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> et <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> qui correspondent aux macros SUCCEEDED et FAILED dans COM.

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

## <a name="iunknown-parameters-passed-as-type-void"></a>Paramètres IUnknown passé comme Type vide
 Recherchez des paramètres [out] qui `void **` sont définis comme le `[``iid_is``]` type [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de l’interface COM, mais qui sont définis comme dans le prototype de méthode d’assemblage interop.

 Parfois, une interface COM `IUnknown` génère un objet, et l’interface COM le passe alors comme type `void **`. Ces interfaces sont particulièrement importantes parce que si la variable est `IUnknown` définie comme [out] dans l’IDL, alors l’objet est compté en référence avec la `AddRef` méthode. Une fuite de mémoire se produit si l’objet n’est pas manipulé correctement.

> [!NOTE]
> Un `IUnknown` objet créé par l’interface COM et retourné dans une variable [out] provoque une fuite de mémoire si elle n’est pas explicitement libérée.

 Les méthodes gérées qui <xref:System.IntPtr> manipulent `IUnknown` ces objets doivent <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> être traitées comme un pointeur d’un objet et appeler la méthode pour obtenir l’objet. L’appelant doit alors présenter la valeur de retour à n’importe quel type approprié. Lorsque l’objet n’est <xref:System.Runtime.InteropServices.Marshal.Release%2A> plus nécessaire, appelez pour le libérer.

 Voici un exemple d’appel de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> méthode et de manipulation correcte de l’objet `IUnknown` :

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
> Les méthodes suivantes sont `IUnknown` connues pour passer <xref:System.IntPtr>les pointeurs d’objets comme type . Manipulez-les comme décrit dans cette section.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Paramètres facultatifs [out]
 Recherchez des paramètres qui sont définis comme`int` `object`un type de données [out] ( , , et ainsi de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] suite) dans l’interface COM, mais qui sont définis comme des tableaux du même type de données dans le prototype de méthode d’assemblage interop.

 Certaines interfaces COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>telles que , traiter [out] paramètres comme facultatif. Si un objet n’est pas nécessaire, ces interfaces COM renvoient un `null` pointeur comme valeur de ce paramètre au lieu de créer l’objet [out]. C'est la procédure normale. Pour ces interfaces, `null` les pointeurs sont supposés dans le cadre du comportement correct de la VSPackage, et aucune erreur n’est retournée.

 Parce que le CLR ne permet pas la `null`valeur d’un paramètre [out] d’être , une partie du comportement conçu de ces interfaces n’est pas directement disponible dans le code géré. Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes d’assemblage interop pour les interfaces affectées fonctionnent autour de la question `null` en définissant les paramètres pertinents comme des tableaux parce que le CLR permet le passage des tableaux.

 Les implémentations gérées de ces méthodes devraient mettre un `null` tableau dans le paramètre quand il n’y a rien à retourner. Sinon, créez un tableau d’un élément du bon type et mettez la valeur de retour dans le tableau.

 Les méthodes gérées qui reçoivent des informations provenant d’interfaces avec des paramètres facultatifs reçoivent le paramètre en tant que tableau. Il suffit d’examiner la valeur du premier élément de la gamme. Si ce `null`n’est pas le cas, traitez le premier élément comme s’il s’agissait du paramètre d’origine.

## <a name="passing-constants-in-pointer-parameters"></a>Passer des constantes dans les paramètres pointeurs
 Recherchez des paramètres qui sont définis comme des pointeurs [dans] <xref:System.IntPtr> dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface COM, mais qui sont définis comme un type dans le prototype de méthode d’assemblage interop.

 Un problème similaire se produit lorsqu’une interface COM passe une valeur spéciale, comme 0, -1, ou -2, au lieu d’un pointeur d’objet. Contrairement [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]à , le CLR ne permet pas constantes d’être jetés comme des objets. Au lieu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de cela, l’assemblage <xref:System.IntPtr> interop définit le paramètre comme un type.

 Les implémentations gérées de ces <xref:System.IntPtr> méthodes `int` devraient `void *` profiter du <xref:System.IntPtr> fait que la classe a à la fois et les constructeurs pour créer un objet ou une constante d’intégration, le cas échéant.

 Les méthodes <xref:System.IntPtr> gérées qui reçoivent des <xref:System.IntPtr> paramètres de ce type doivent utiliser les opérateurs de conversion de type pour gérer les résultats. Convertissez <xref:System.IntPtr> d’abord le totger `int` et le testez contre les constantes d’intégreurs pertinentes. Si aucune valeur ne correspond, convertissez-la en un objet du type requis et continuez.

 Pour des exemples <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>de cela, voir et .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valeurs de retour OLE passé comme paramètres [out]
 Recherchez des méthodes `retval` qui ont une valeur de `int` retour dans l’interface COM, mais [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui ont une valeur de retour et un paramètre de tableau supplémentaire [out] dans le prototype de méthode d’assemblage interop. Il devrait être clair que ces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes nécessitent une manipulation spéciale parce que les prototypes de méthode d’assemblage interop ont un paramètre de plus que les méthodes d’interface COM.

 De nombreuses interfaces COM qui traitent de l’activité OLE envoient `retval` des informations sur le statut OLE au programme d’appels stocké dans la valeur de retour de l’interface. Au lieu d’utiliser une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valeur de retour, les méthodes d’assemblage interop correspondantes renvoient l’information au programme d’appels stocké dans un paramètre de tableau [out].

 Les implémentations gérées de ces méthodes devraient créer un tableau d’un seul élément du même type que le paramètre [out] et le mettre dans le paramètre. La valeur de l’élément de tableau `retval`doit être la même que la COM appropriée .

 Les méthodes gérées qui appellent les interfaces de ce type devraient retirer le premier élément du tableau [out]. Cet élément peut être traité comme `retval` s’il s’agissait d’une valeur de retour de l’interface COM correspondante.

## <a name="see-also"></a>Voir aussi
- [Interopération avec code non traité](/dotnet/framework/interop/index)

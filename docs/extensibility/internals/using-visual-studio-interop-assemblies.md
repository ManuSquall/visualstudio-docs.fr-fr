---
title: "L’utilisation d’assemblys PIA Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>À l’aide d’assemblys PIA de Visual Studio
Assemblys PIA de Visual Studio permettent aux applications managées accéder aux interfaces COM qui fournissent une extensibilité de Visual Studio. Il existe certaines différences entre les interfaces COM directement et leurs versions interop. Par exemple, HRESULT sont généralement représentées sous forme de valeurs de type int et doivent être traitées de la même façon en tant qu’exceptions et les paramètres (en particulier les paramètres de sortie) sont traités différemment.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestion des HRESULT retournés au code managé à partir de COM  
 Quand vous appelez une interface COM à partir de code managé, examinez la valeur HRESULT et levez une exception si nécessaire. La <xref:Microsoft.VisualStudio.ErrorHandler>classe contenant la <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>méthode qui lève une exception COM, selon la valeur de HRESULT passé à celui-ci.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 Par défaut, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>lève une exception lorsqu’elle est passée à une valeur HRESULT qui a une valeur inférieure à zéro.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Dans les cas où ces valeurs HRESULT sont des valeurs acceptables et aucune exception ne doit être levée, les valeurs des HRESULTS supplémentaire doivent être transmis à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>une fois que les valeurs sont testées.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Si la valeur HRESULT qui est testé correspond à toutes les valeurs HRESULT passées explicitement à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, aucune exception n’est levée.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  La <xref:Microsoft.VisualStudio.VSConstants>classe contient les constantes pour les valeurs HRESULT courantes, par exemple, <xref:Microsoft.VisualStudio.VSConstants.S_OK>et <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>et <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>fournit également les <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>et les <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>méthodes, qui correspondent aux macros réussite et échec dans COM.</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> </xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Par exemple, considérez l’appel de fonction suivant, dans lequel <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>est une valeur de retournée acceptable, mais les autres HRESULT inférieure à zéro représente une erreur.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[N °&1; de VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n °&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 S’il existe plusieurs valeurs de retournés possibles, les valeurs HRESULT supplémentaires peuvent uniquement être ajoutés à la liste dans l’appel à <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
 [!code-vb[VSSDKHRESULTInformation n °&2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n °&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Retour de valeurs HRESULT à COM à partir de code managé  
 Si aucune exception ne se produit, le code managé retourne <xref:Microsoft.VisualStudio.VSConstants.S_OK>à la fonction COM qui a appelé celui-ci.</xref:Microsoft.VisualStudio.VSConstants.S_OK> COM interop prend en charge les exceptions courantes qui sont fortement typées dans du code managé. Par exemple, une méthode qui reçoit un inacceptable `null` argument lève un <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Si vous ne savez pas quelle exception levée, mais que vous connaissez la valeur HRESULT que vous souhaitez revenir à COM, vous pouvez utiliser la <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>méthode pour lever une exception appropriée.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Cela fonctionne même avec une erreur non standard, par exemple, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>tente de mapper des HRESULT lui sont transmises à une exception fortement typée.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Si ce n’est pas possible, une exception COM générique est levée. Le résultat final est que la valeur HRESULT que vous transmettez à <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>du code managé est retournée à la fonction COM qui a appelé celui-ci.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  Les exceptions nuisent aux performances et ont vocation à indiquer des conditions anormales pour le programme. Les conditions qui se produisent souvent doivent être gérées instantanément, au lieu de lever une exception.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>Paramètres de IUnknown passés en tant que Type void **  
 Recherchez les [paramètres qui sont définis en tant que type out] `void **` dans le modèle COM interface, mais qui sont définis en tant que `[``iid_is``]` dans les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
 Parfois, une interface COM génère une `IUnknown` objet et l’interface COM puis passe en tant que type `void **`. Ces interfaces sont particulièrement importants, car si la variable est définie en tant que [out] dans le fichier IDL, la `IUnknown` objet est comptée par référence avec le `AddRef` (méthode). Une fuite de mémoire se produit si l’objet n’est pas gérée correctement.  
  
> [!NOTE]
>  Un `IUnknown` objet créé par l’interface COM et retournée dans une variable [out] entraîne une fuite de mémoire si elle n’est pas explicitement libéré.  
  
 Les méthodes managées qui gèrent ces objets doit être traitée <xref:System.IntPtr>comme un pointeur vers un `IUnknown` et appelez le <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>méthode pour obtenir l’objet.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> L’appelant doit alors convertir la valeur de retour de tout type est approprié. Lorsque l’objet n’est plus nécessaire, appelez <xref:System.Runtime.InteropServices.Marshal.Release%2A>à la relâchez.</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 Voici un exemple de l’appel de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>méthode et la gestion de la `IUnknown` correctement l’objet :</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
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
>  Les méthodes suivantes sont connus pour passer `IUnknown` des pointeurs d’objet en tant que type <xref:System.IntPtr>.</xref:System.IntPtr> Traitez-les comme décrit dans cette section.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Facultatif de [paramètres out]  
 Recherchez les paramètres qui sont définis en tant que [out] type de données (`int`, `object`, et ainsi de suite) dans le modèle COM interface, mais qui sont définis en tant que tableaux du même type de données dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
 Certains COM des interfaces, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, traiter les [paramètres comme étant facultatifs out].</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Si un objet n’est pas nécessaire, ces interfaces COM retournent un `null` pointeur en tant que la valeur de ce paramètre au lieu de créer l’objet [out]. Ceci est normal. Pour ces interfaces, `null` les pointeurs sont supposés en tant que partie du comportement correct du VSPackage, et aucune erreur n’est retournée.  
  
 Étant donné que le CLR n’autorise pas la valeur d’un paramètre [out] d’être `null`, le comportement de ces interfaces conçues n’est pas directement disponible dans le code managé. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes d’assembly d’interopérabilité pour les interfaces affectés contourner le problème en définissant les paramètres pertinents en tant que tableaux, car le CLR permet le passage de `null` tableaux.  
  
 Des implémentations managées de ces méthodes doivent placer un `null` tableau dans le paramètre lorsqu’il n’y a rien à retourner. Sinon, créez un tableau d’un élément du type correct et placer la valeur de retour dans le tableau.  
  
 Méthodes qui reçoivent des informations à partir d’interfaces avec [out] facultatif managées paramètres reçoivent le paramètre sous forme de tableau. Il suffit d’examiner la valeur du premier élément du tableau. Si ce n’est pas `null`, traite le premier élément comme s’il était le paramètre d’origine.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Constantes de passage de paramètres de pointeur  
 Recherchez les paramètres qui sont définis comme [in] pointeurs dans l’interface COM, mais qui sont définies comme un <xref:System.IntPtr>type dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly PIA.</xref:System.IntPtr>  
  
 Un problème similaire se produit lorsqu’une interface COM transmet une valeur spéciale, tel que 0, -1 ou – 2, au lieu d’un pointeur d’objet. Contrairement à [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], le CLR n’autorise pas les constantes à être casté en tant qu’objets. Au lieu de cela, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly PIA définit le paramètre comme un <xref:System.IntPtr>type.</xref:System.IntPtr>  
  
 Des implémentations managées de ces méthodes doivent tirer parti du fait que la <xref:System.IntPtr>classe a deux `int` et `void *` constructeurs pour créer un <xref:System.IntPtr>à partir d’un objet ou une constante entière, comme il convient.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Géré les méthodes qui reçoivent <xref:System.IntPtr>paramètres de ce type doivent utiliser le <xref:System.IntPtr>pour gérer les résultats des opérateurs de conversion de type.</xref:System.IntPtr> </xref:System.IntPtr> Tout d’abord convertir le <xref:System.IntPtr>à `int` et la tester avec des constantes entières pertinentes.</xref:System.IntPtr> Si aucune valeur ne correspondre, convertissez-le en un objet du type requis et continuer.  
  
 Pour des exemples, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE retourner valeurs passées comme [paramètre out]  
 Recherchez des méthodes qui ont un `retval` valeur de retour dans l’interface COM, mais qui ont une `int` retourner de valeur et supplémentaire [out] le paramètre de tableau dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototype de méthode d’assembly d’interopérabilité. Il doit être clair que ces méthodes requièrent un traitement spécial, car le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypes de méthode d’assembly d’interopérabilité ont un paramètre de plus que les méthodes d’interface COM.  
  
 Nombreuses interfaces COM qui traitent de l’activité OLE envoyer des informations sur l’état OLE au programme appelant stocké dans la `retval` valeur de retour de l’interface. Au lieu d’utiliser une valeur de retour correspondantes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] méthodes de l’assembly PIA envoient les informations au programme appelant stocké dans [out] paramètre de tableau.  
  
 Des implémentations managées de ces méthodes doivent créer un seul élément tableau du même type que le paramètre [out] et placez-le dans le paramètre. La valeur de l’élément de tableau doit être le même que le modèle COM approprié `retval`.  
  
 Les méthodes managées qui appellent les interfaces de ce type doivent extraire le premier élément hors du tableau [out]. Cet élément peut être traité comme si elle était un `retval` valeur de retour à partir de l’interface COM correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du Code non managé](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

---
title: Marshaling des paramètres de l’assembly d’interopérabilité Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686926"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Marshaling des paramètres d’assembly PIA Visual Studio
Les VSPackages écrits en code managé peuvent devoir appeler ou être appelés par du code COM non managé. En règle générale, les arguments de méthode sont transformés, ou marshalés, automatiquement par le marshaleur d’interopérabilité. Toutefois, parfois, les arguments ne peuvent pas être transformés de manière simple. Dans ces cas, les paramètres de prototype de méthode d’assembly d’interopérabilité sont utilisés pour faire correspondre les paramètres de fonction COM le plus fidèlement possible. Pour plus d’informations, consultez la page [marshaling d’interopérabilité](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Suggestions générales  
  
##### <a name="read-the-reference-documentation"></a>Lire la documentation de référence  
 Une méthode efficace pour détecter les problèmes d’interopérabilité consiste à lire la documentation de référence pour chaque méthode.  
  
 La documentation de référence pour chaque méthode contient trois sections pertinentes :  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Prototype de fonction com.  
  
- Prototype de méthode de l’assembly d’interopérabilité.  
  
- Liste des paramètres COM et une brève description de chacun d’eux.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Rechercher les différences entre les deux prototypes  
 La plupart des problèmes d’interopérabilité dérivent des incompatibilités entre la définition d’un type particulier dans une interface COM et la définition du même type dans les [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assemblys d’interopérabilité. Par exemple, considérez la différence dans la possibilité de passer une `null` valeur dans un paramètre [out]. Vous devez rechercher les différences entre les deux prototypes et prendre en compte leurs ramifications pour les données transmises.  
  
##### <a name="read-the-parameter-definitions"></a>Lire les définitions de paramètre  
 Lisez les définitions des paramètres. COM est moins strict que le common language runtime (CLR) sur la combinaison de différents types de données dans un seul paramètre. Les [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaces com tirent pleinement parti de cette flexibilité. Tout paramètre qui peut passer ou exiger une valeur non standard ou un type de données, tel qu’une valeur de constante dans un paramètre de pointeur, doit être décrit comme tel dans la documentation.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Objets IUnknown passés en tant que type void * *  
 Recherchez les paramètres [out] définis en tant que type `void **` dans l’interface com, mais qui sont définis comme `[``iid_is``]` dans le prototype de la méthode de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité.  
  
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
  
### <a name="optional-out-parameters"></a>Paramètres facultatifs [out]  
 Recherchez les paramètres définis en tant que type de données [out] ( `int` , `object` , etc.) dans l’interface com, mais qui sont définis en tant que tableaux du même type de données dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
 Certaines interfaces COM, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , traitent les paramètres [out] comme facultatifs. Si un objet n’est pas requis, ces interfaces COM retournent un `null` pointeur comme valeur de ce paramètre au lieu de créer l’objet [out]. C'est la procédure normale. Pour ces interfaces, les `null` pointeurs sont considérés comme faisant partie du comportement correct du VSPackage et aucune erreur n’est retournée.  
  
 Étant donné que le CLR n’autorise pas la valeur d’un paramètre [out] `null` , une partie du comportement conçu de ces interfaces n’est pas directement disponible dans le code managé. Les [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] méthodes d’assembly d’interopérabilité pour les interfaces affectées contournent le problème en définissant les paramètres appropriés en tant que tableaux, car le CLR autorise le passage de `null` tableaux.  
  
 Les implémentations managées de ces méthodes doivent placer un `null` tableau dans le paramètre lorsqu’il n’y a rien à retourner. Sinon, créez un tableau d’un élément du type correct et placez la valeur de retour dans le tableau.  
  
 Les méthodes managées qui reçoivent des informations à partir d’interfaces avec des paramètres facultatifs [out] reçoivent le paramètre sous la forme d’un tableau. Examinez simplement la valeur du premier élément du tableau. Si ce n’est pas le cas `null` , traite le premier élément comme s’il s’agissait du paramètre d’origine.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Passage de constantes dans des paramètres de pointeur  
 Recherchez les paramètres définis en tant que pointeurs [in] dans l’interface COM, mais qui sont définis en tant que <xref:System.IntPtr> type dans le prototype de méthode de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité.  
  
 Un problème similaire se produit lorsqu’une interface COM passe une valeur spéciale, telle que 0,-1 ou-2, au lieu d’un pointeur d’objet. Contrairement [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] à, le CLR n’autorise pas le cast des constantes en tant qu’objets. Au lieu de cela, l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité définit le paramètre en tant que <xref:System.IntPtr> type.  
  
 Les implémentations managées de ces méthodes doivent tirer parti du fait que la <xref:System.IntPtr> classe a `int` des `void *` constructeurs et pour créer un <xref:System.IntPtr> à partir d’un objet ou d’une constante entière, le cas échéant.  
  
 Les méthodes managées qui reçoivent <xref:System.IntPtr> des paramètres de ce type doivent utiliser les <xref:System.IntPtr> opérateurs de conversion de type pour gérer les résultats. Tout d’abord, convertissez le <xref:System.IntPtr> en `int` et testez-le par rapport aux constantes entières appropriées. Si aucune valeur ne correspond, convertissez-la en un objet du type requis et continuez.  
  
 Pour obtenir des exemples, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Valeurs de retour OLE passées en tant que paramètres [out]  
 Recherchez les méthodes qui ont une `retval` valeur de retour dans l’interface com, mais qui ont une `int` valeur de retour et un paramètre de tableau [out] supplémentaire dans le prototype de méthode de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité. Il doit être clair que ces méthodes nécessitent un traitement spécial, car les [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypes de méthode de l’assembly d’interopérabilité ont un paramètre de plus que les méthodes de l’interface com.  
  
 De nombreuses interfaces COM qui gèrent l’activité OLE envoient des informations sur l’État OLE au programme appelant stocké dans la `retval` valeur de retour de l’interface. Au lieu d’utiliser une valeur de retour, les méthodes de l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité correspondant renvoient les informations au programme appelant stocké dans un paramètre de tableau [out].  
  
 Les implémentations managées de ces méthodes doivent créer un tableau à un seul élément du même type que le paramètre [out] et les placer dans le paramètre. La valeur de l’élément de tableau doit être la même que le COM approprié `retval` .  
  
 Les méthodes managées qui appellent des interfaces de ce type doivent extraire le premier élément du tableau [out]. Cet élément peut être traité comme s’il s’agissait `retval` d’une valeur de retour de l’interface com correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Marshaling d’interopérabilité](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshaling d’interopérabilité](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Résolution des problèmes d’interopérabilité](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackages gérés](../misc/managed-vspackages.md)
---
title: Paramètres d’Assembly PIA Visual Studio Marshaling | Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686926"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Marshaling des paramètres d’assembly PIA Visual Studio
Les VSPackages sont écrits en code managé peut devoir appeler ou être appelé par du code COM non managé. En règle générale, les arguments de méthode sont transformées ou marshalés, automatiquement par le marshaleur d’interopérabilité. Cependant, parfois arguments ne peuvent pas être transformées de manière simple. Dans ce cas, les paramètres de prototype de méthode assembly d’interopérabilité sont utilisés pour faire correspondre les paramètres de la fonction COM aussi fidèlement que possible. Pour plus d’informations, consultez [Marshaling d’interopérabilité](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Suggestions d’ordre général  
  
##### <a name="read-the-reference-documentation"></a>Lire la documentation de référence  
 Un moyen efficace pour détecter les problèmes d’interopérabilité consiste à lire la documentation de référence pour chaque méthode.  
  
 La documentation de référence pour chaque méthode contient trois sections correspondantes :  
  
- Le [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] prototype de fonction COM.  
  
- Le prototype de méthode d’assembly d’interopérabilité.  
  
- Une liste des paramètres COM et une brève description de chacun d’eux.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Rechercher les différences entre les deux prototypes  
 La plupart des problèmes d’interopérabilité dérivent des incompatibilités entre la définition d’un type particulier dans une interface COM et la définition du même type dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assemblys d’interopérabilité. Par exemple, considérez la différence dans la capacité à passer un `null` valeur dans un paramètre [out]. Vous devez rechercher les différences entre les deux prototypes et prendre en compte leurs conséquences pour les données transmises.  
  
##### <a name="read-the-parameter-definitions"></a>Lire les définitions de paramètres  
 Lire les définitions de paramètres. COM est moins stricte que le common language runtime (CLR) sur la combinaison de différents types de données dans un seul paramètre. Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaces COM tirer pleinement parti de cette flexibilité. N’importe quel paramètre qui peut transmettre ou nécessitent une valeur non standard ou un type de données, telle qu’une valeur constante dans un paramètre de pointeur, doit être décrits en tant que tel, dans la documentation.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown objets passés en tant que Type void **  
 Recherchez les [paramètres qui sont définis en tant que type out] `void **` dans le modèle COM interface, mais qui sont définis comme `[``iid_is``]` dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
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
  
### <a name="optional-out-parameters"></a>Facultatif de [paramètres out]  
 Recherchez les paramètres qui sont définis en tant que [out] type de données (`int`, `object`, et ainsi de suite) dans le modèle COM interface, mais qui sont définis en tant que tableaux du même type de données dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
 Certains COM des interfaces, telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, traiter les [paramètres comme étant facultatifs out]. Si un objet n’est pas requis, le retour de ces interfaces COM une `null` pointeur en tant que la valeur de ce paramètre au lieu de créer l’objet [out]. Ceci est normal. Pour ces interfaces, `null` pointeurs sont supposées en tant que partie du comportement correct du VSPackage, et aucune erreur n’est retournée.  
  
 Étant donné que le CLR n’autorise pas la valeur de paramètre [out] pour être `null`, partie du comportement de ces interfaces conçu n’est pas directement disponible dans du code géré. Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] méthodes d’assembly d’interopérabilité pour les interfaces affectés contournent le problème en définissant les paramètres pertinents en tant que tableaux, car le CLR permet la transmission de `null` tableaux.  
  
 Les implémentations managées de ces méthodes doivent placer un `null` tableau dans le paramètre quand il n’y a rien à retourner. Sinon, créez un tableau d’un élément du type correct et placer la valeur de retour dans le tableau.  
  
 Gérés des méthodes qui reçoivent des informations à partir d’interfaces avec facultatif [out] Paramètres reçoivent le paramètre sous forme de tableau. Il suffit d’examiner la valeur du premier élément du tableau. Si ce n’est pas `null`, traiter le premier élément comme s’il était le paramètre d’origine.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Constantes de passage de paramètres de pointeur  
 Recherchez les paramètres qui sont définies comme [in] pointeurs dans l’interface COM, mais qui sont définies comme un <xref:System.IntPtr> tapez dans la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototype de méthode d’assembly d’interopérabilité.  
  
 Un problème similaire se produit lorsqu’une interface COM transmet une valeur spéciale, telles que 0, -1 ou – 2, au lieu d’un pointeur d’objet. Contrairement à [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], le CLR n’autorise pas les constantes à être casté en tant qu’objets. Au lieu de cela, le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly d’interopérabilité définit le paramètre comme un <xref:System.IntPtr> type.  
  
 Des implémentations managées de ces méthodes doivent tirer parti du fait que le <xref:System.IntPtr> classe dispose à la fois `int` et `void *` constructeurs pour créer un <xref:System.IntPtr> à partir d’un objet ou une constante entière, comme il convient.  
  
 Gérés des méthodes qui reçoivent <xref:System.IntPtr> paramètres de ce type doivent utiliser le <xref:System.IntPtr> des opérateurs de conversion pour gérer les résultats de type. Tout d’abord convertir le <xref:System.IntPtr> à `int` et testez-le par rapport à des constantes entières pertinentes. Si aucune valeur ne correspondre, la convertir en un objet du type requis et continuer.  
  
 Pour des exemples, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE retourner valeurs passées comme [paramètre out]  
 Recherchez les méthodes qui ont un `retval` valeur de retour dans l’interface COM, mais qui ont un `int` valeur de retour et un autre [paramètre de tableau dans out] le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototype de méthode d’assembly d’interopérabilité. Il doit être clair que ces méthodes nécessitent une gestion spéciale, car le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypes de méthode d’assembly d’interopérabilité ont un paramètre supplémentaire que les méthodes d’interface COM.  
  
 Nombre d’interfaces COM qui traitent de l’activité OLE envoyer des informations sur l’état OLE revenir au programme appelant stocké dans le `retval` retourner la valeur de l’interface. Au lieu d’utiliser une valeur de retour correspondants [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] méthodes de l’assembly d’interopérabilité envoient les informations au programme appelant stocké dans un paramètre [out] paramètre de tableau.  
  
 Les implémentations managées de ces méthodes doivent créer un seul élément tableau du même type que le paramètre [out] et le placer dans le paramètre. La valeur de l’élément de tableau doit être le même que le modèle COM approprié `retval`.  
  
 Les méthodes managées qui appellent les interfaces de ce type doivent extraire le premier élément hors du tableau [out]. Cet élément peut être traité comme s’il s’agissait d’un `retval` valeur de retour à partir de l’interface COM correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Marshaling d’interopérabilité](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshaling d’interopérabilité](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Résolution des problèmes d’interopérabilité](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackages gérés](../misc/managed-vspackages.md)
---
title: Rendre les projets personnalisés prenant en charge les Version | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5b2cfb51ad13ed28e1f021b19b52153bf4c09f62
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948923"
---
# <a name="making-custom-projects-version-aware"></a>Prise en charge des versions dans les projets personnalisés
Dans votre système de projet personnalisé, vous pouvez faire en sorte que les projets de ce type se chargent dans plusieurs versions de Visual Studio. Vous pouvez aussi empêcher les projets de ce type de se charger dans une version antérieure de Visual Studio. De même, vous pouvez permettre à un projet de s’identifier dans une version ultérieure dans le cas où il aurait besoin d’être réparé, converti ou désapprouvé.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Autorisation du chargement de projets dans plusieurs versions  
 Vous pouvez modifier la plupart des projets qui ont été créés dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] avec SP1 ou une version ultérieure de façon à les faire fonctionner dans plusieurs versions.  
  
 Avant de charger un projet, Visual Studio appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> pour déterminer si le projet peut être mis à niveau. Si c’est le cas, la méthode `UpgradeProject_CheckOnly` définit un indicateur qui provoque un appel ultérieur à la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> pour mettre à niveau le projet. Sachant que les projets incompatibles ne peuvent pas être mis à niveau, `UpgradeProject_CheckOnly` doit d’abord vérifier que le projet est compatible, comme l’indique la section précédente.  
  
 En tant qu’auteur d’un système de projet, vous devez implémenter `UpgradeProject_CheckOnly` (à partir de l’interface `IVsProjectUpgradeViaFactory4` ) pour permettre aux utilisateurs de votre système de projet de vérifier les possibilités de mise à niveau. Quand les utilisateurs ouvrent un projet, cette méthode est appelée pour déterminer si un projet doit être réparé avant d’être chargé. Les conditions possibles de mise à niveau sont énumérées dans `VSPUVF_REPAIRFLAGS`; voici les différentes possibilités :  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Aucune réparation n’est nécessaire.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Rend le projet compatible avec une version antérieure sans les problèmes que vous pouvez être exposé avec les versions précédentes du produit.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Rend le projet rétrocompatible tout à certains des problèmes que vous auriez pu rencontrer avec les versions précédentes du produit. Par exemple, le projet ne sera pas compatible s’il dépend de différentes versions de Kit de développement logiciel (SDK).  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Rend le projet incompatible avec une version antérieure.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Indique que la version actuelle ne prend en charge ce projet.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Indique que ce projet n’est plus pris en charge.  
  
> [!NOTE]
>  Pour éviter toute confusion, ne définissez pas plusieurs indicateurs de mise à niveau. Par exemple, ne créez pas un état de mise à niveau ambigu tel que `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Certaines versions du projet peuvent implémenter la fonction `UpgradeProjectFlavor_CheckOnly` de l’interface `IVsProjectFlavorUpgradeViaFactory2` . Pour que cette fonction soit opérationnelle, elle doit être appelée par l’implémentation de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` mentionnée précédemment. Cet appel est déjà implémenté dans le système de projet de base Visual Basic ou C#. L’effet de cette fonction permet aux versions du projet de déterminer aussi les conditions de mise à niveau d’un projet, en plus de ce que le système de projet de base a déterminé. La boîte de dialogue de compatibilité indique les deux conditions les plus contraignantes.  
  
 Quand Visual Studio procède à une vérification de mise à niveau, il fournit un enregistreur d’événements et non une valeur NULL, comme dans les versions précédentes de Visual Studio. L’enregistreur d’événements permet aux systèmes et versions de  projet de fournir des informations supplémentaires qui peuvent vous aider à comprendre la nature des modifications à apporter pour que vos anciens projets se chargent correctement. Nous vous recommandons d’utiliser l’enregistreur d’événements pour fournir des informations supplémentaires au lieu d’utiliser des boîtes de dialogue. Pour plus d’informations, consultez [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) plus loin dans cette rubrique.  
  
 Pour des implémentations managées, les interfaces de mise à niveau de projet sont disponibles dans l’assembly d’interopérabilité Microsoft.VisualStudio.Shell.Interop.11.0.dll.  
  
 La méthode `UpgradeProject` peut déterminer si les modifications qu’elle apporte empêcheraient le projet de se charger dans une version antérieure de Visual Studio. Si tel est le cas, la méthode marque le projet comme étant incompatible. Pour comprendre comment un projet est marqué « incompatible », consultez [Marking a Project as Incompatible](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) plus haut dans cette rubrique. Nous vous recommandons de marquer le projet comme étant incompatible dès l’affichage de cette boîte de dialogue en appelant directement la méthode `IVsAppCompat.BreakAssetCompatibility` , au lieu d’appeler d’abord la méthode `IVsAppCompat.AskForUserConsentToBreakAssetCompat` , car la boîte de dialogue n’a pas besoin d’être affichée deux fois.  
  
 Voici un exemple qui résume l’expérience utilisateur de la boîte de dialogue de compatibilité. Si un projet a été créé dans une version antérieure et que la version actuelle détermine qu’une mise à niveau est nécessaire, Visual Studio affiche une boîte de dialogue pour demander à l’utilisateur l’autorisation d’apporter les modifications. Si l’utilisateur accepte, le projet est modifié puis chargé. Si la solution est ensuite fermée et rouverte dans une version antérieure, le projet ayant fait l’objet d’une mise à niveau définitive devient incompatible et ne se charge pas. Si le projet nécessite seulement une réparation (et non une mise à niveau), le projet réparé continue de s’ouvrir dans les deux versions.  
  
##  <a name="BKMK_Incompat"></a> Marquage d’un projet comme étant Incompatible  
 Vous pouvez marquer un projet comme étant incompatible avec les versions antérieures de Visual Studio.  Par exemple, supposons que vous créez un projet qui utilise une fonctionnalité de .NET Framework 4.5. Comme ce projet ne peut pas être généré dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], vous pouvez le marquer comme étant incompatibles pour empêcher cette version de le charger.  
  
 Le composant qui ajoute la fonctionnalité incompatible est chargé de marquer le projet comme étant incompatible. Le composant doit avoir accès à l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> qui représente les projets qui présentent un intérêt.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Pour marquer un projet comme étant incompatible  
  
1.  Dans le composant, obtenez une interface `IVsAppCompat` auprès du service global SVsSolution.  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  Dans le composant, appelez `IVsAppCompat.AskForUserConsentToBreakAssetCompat`, puis passez-lui un tableau d’interfaces `IVsHierarchy` qui représentent les projets dignes d’intérêt.  
  
     Cette méthode a la signature suivante :  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Si vous implémentez ce code, une boîte de dialogue de compatibilité de projet s’affiche. Cette boîte de dialogue demande à l’utilisateur l’autorisation de marquer tous les projets spécifiés comme étant incompatibles. Si l’utilisateur accepte, `AskForUserConsentToBreakAssetCompat` retourne `S_OK`; sinon, `AskForUserConsentToBreakAssetCompat` retourne `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  Dans les scénarios les plus courants, le tableau `IVsHierarchy` contient un seul élément.  
  
3.  Si `AskForUserConsentToBreakAssetCompat` retourne `S_OK`, le composant apporte ou accepte les modifications qui mettent fin à la compatibilité.  
  
4.  Dans votre composant, appelez la méthode `IVsAppCompat.BreakAssetCompatibility` pour chaque projet à marquer comme étant incompatible. Au lieu de laisser Visual Studio rechercher la chaîne de la version actuelle dans le Registre, le composant peut attribuer une valeur au paramètre `lpszMinimumVersion` qui correspond à une version minimale spécifique. Cette approche réduit le risque de voir à un moment ultérieur le composant définir par inadvertance une valeur supérieure, en fonction de ce qui est inscrit dans le Registre à ce moment-là. La définition d’une valeur supérieure empêcherait Visual Studio d’ouvrir le projet.  
  
     Cette méthode a la signature suivante :  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Si le composant attribue à `lpszMinimumVersion` la valeur NULL, la méthode `BreakAssetCompatibility` appelle la méthode `IVsAppCompat.GetCurrentDesignTimeCompatVersion` pour obtenir une chaîne qui représente la version actuelle de Visual Studio.  
  
     Cette méthode a la signature suivante :  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     La méthode BreakAssetCompatibility appelle ensuite la méthode `IVsHierarchy.SetProperty` pour attribuer à la propriété racine `VSHPROPID_MinimumDesignTimeCompatVersion` la valeur de la chaîne de version que vous avez obtenue à l’étape précédente.  
  
     Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Vous devez implémenter la propriété `VSHPROPID_MinimumDesignTimeCompatVersion` pour marquer un projet comme étant compatible ou incompatible. Par exemple, si le système de projet utilise un fichier projet MSBuild, ajoutez au fichier projet une propriété de build `<MinimumVisualStudioVersion>` dont la valeur est égale à la valeur de la propriété `VSHPROPID_MinimumDesignTimeCompatVersion` correspondante.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Détection d’une incompatibilité de projet  
 Un projet qui n’est pas compatible avec la version actuelle de Visual Studio ne doit pas être chargé. De plus, il ne peut ni être mis à niveau ni réparé. Par conséquent, la compatibilité d’un projet doit être vérifiée à deux moments : le première, quand il s’agit de déterminer s’il doit être mis à niveau ou réparé et le deuxième, avant son chargement.  
  
 Pour permettre la détection d’une incompatibilité de projet, vous devez implémenter les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Si le projet est incompatible, `UpgradeProject_CheckOnly` doit retourner le code de réussite `VS_S_INCOMPATIBLEPROJECT`et `CreateProject` le code d’erreur `VS_E_INCOMPATIBLEPROJECT`. Pour les projets ayant différentes versions, vous devez implémenter `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` au lieu de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Un système de projet est dit à plusieurs versions s’il intègre un type de projet web, Office (VSTO), Silverlight ou autre. Les anciens systèmes de projet qui implémentent déjà `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` et les systèmes de projet à plusieurs versions qui implémentent déjà `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` continuent d’être pris en charge. L’ancienne version de `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` a la signature d’implémentation suivante :  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Si cette méthode attribue à `pUpgradeRequired` la valeur TRUE et retourne `S_OK`, le résultat est considéré comme une « Mise à niveau » et comme si la méthode attribuait à un indicateur de mise à niveau la valeur `VSPUVF_PROJECT_ONEWAYUPGRADE`, qui est décrite plus loin dans cette rubrique. Les valeurs de retour suivantes sont prises en charge en utilisant cette ancienne méthode, mais seulement quand `pUpgradeRequired` a la valeur TRUE :  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Cette valeur de retour traduit la valeur `pUpgradeRequired` en valeur TRUE qui est l’équivalent de `VSPUVF_PROJECT_SAFEREPAIR`, dont vous trouverez la description plus loin dans cette rubrique.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Cette valeur de retour traduit la valeur `pUpgradeRequired` en valeur TRUE qui est l’équivalent de `VSPUVF_PROJECT_UNSAFEREPAIR`, dont vous trouverez la description plus loin dans cette rubrique.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Cette valeur de retour traduit la valeur `pUpgradeRequired` en valeur TRUE qui est l’équivalent de `VSPUVF_PROJECT_ONEWAYUPGRADE`, dont vous trouverez la description plus loin dans cette rubrique.  
  
   Les nouvelles implémentations dans `IVsProjectUpgradeViaFactory4` et `IVsProjectFlavorUpgradeViaFactory2` permettent de spécifier le type de migration avec davantage de précision.  
  
> [!NOTE]
>  Vous pouvez mettre en cache le résultat de la vérification de compatibilité exécutée par la méthode `UpgradeProject_CheckOnly` de sorte que le prochain appel à `CreateProject`puisse aussi l’utiliser.  
  
 Par exemple, si les méthodes `UpgradeProject_CheckOnly` et `CreateProject` qui sont écrites pour un système de projet [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] avec SP1 examinent un fichier projet et déterminent que la propriété de build `<MinimumVisualStudioVersion>` a la valeur « 11.0 », Visual Studio 2010 SP1 ne charge pas le projet. De plus, **Solution Navigator** indique que le projet est « incompatible » et ne le charge pas.  
  
##  <a name="BKMK_UpgradeLogger"></a> Le journal de mise à niveau  
 L’appel à `IVsProjectUpgradeViaFactory::UpgradeProject` contient un enregistreur d’événements `IVsUpgradeLogger` que les systèmes et versions de projet doivent utiliser pour fournir un suivi de mise à niveau détaillé à des fins de dépannage. Si un avertissement ou une erreur est consigné, Visual Studio affiche le rapport de mise à niveau.  
  
 Quand vous écrivez dans l’enregistreur d’événements de mise à niveau, tenez compte des indications suivantes :  
  
-   Visual Studio appelle Flush une fois que la mise à niveau de tous les projets est terminée. Ne l’appelez pas dans votre système de projet.  
  
-   La fonction LogMessage présente les niveaux d’erreur suivants :  
  
    -   0 correspond aux informations dont vous voulez assurer le suivi.  
  
    -   1 correspond à un avertissement.  
  
    -   2 correspond à une erreur.  
  
    -   3 correspond au formateur de rapport. Une fois que votre projet est mis à niveau, consignez le mot « Converted » une seule fois, sans le traduire.  
  
-   Si un projet ne nécessite aucune réparation ou mise à niveau, Visual Studio ne génère le fichier journal que si le système de projet a consigné un avertissement ou une erreur pendant l’exécution de la méthode UpgradeProject_CheckOnly ou UpgradeProjectFlavor_CheckOnly.
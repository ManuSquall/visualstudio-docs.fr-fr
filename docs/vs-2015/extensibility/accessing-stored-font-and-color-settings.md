---
title: Accès aux paramètres des polices et des couleurs stockées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821829"
---
# <a name="accessing-stored-font-and-color-settings"></a>Accès aux paramètres de police et de couleur stockés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE) stocke les paramètres modifiés pour les polices et les couleurs dans le registre. Vous pouvez utiliser l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface pour accéder à ces paramètres.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Pour initier la persistance de l’état des polices et des couleurs  
 Les informations de police et de couleur sont stockées par catégorie dans l’emplacement de Registre suivant : [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], où *\<CategoryGUID>* est le GUID de la catégorie.  
  
 Par conséquent, pour initialiser la persistance, un VSPackage doit :  
  
- Obtenez une <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface en appelant `QueryService` auprès du fournisseur de services global.  
  
     `QueryService` doit être appelé à l’aide d’un argument d’ID de service `SID_SVsFontAndColorStorage` et d’un argument d’ID d’interface de `IID_IVsFontAndColorStorage` .  
  
- Utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode pour ouvrir une catégorie à rendre persistante en utilisant le GUID de la catégorie et un indicateur de mode comme arguments.  
  
  Le mode, spécifié par l' `fFlags` argument, est construit à partir des valeurs de l' <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> énumération. Ce mode contrôle :  

  - Paramètres accessibles par le biais de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  

  - Soit tous les paramètres, soit uniquement ceux que les utilisateurs modifient et sont récupérables via l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  

  - Méthode de propagation des modifications apportées aux paramètres utilisateur.  

  - Format des valeurs de couleur utilisées.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Pour utiliser la persistance de l’état des polices et des couleurs  
 La persistance des polices et des couleurs implique :  
  
- Synchronisation des paramètres IDE avec les paramètres stockés dans le registre.  
  
- Propagation des informations de modification du Registre.  
  
- Définition et récupération des paramètres stockés dans le registre.  
  
  La synchronisation du paramètre de stockage avec les paramètres de l’IDE est en grande partie transparente. L’IDE sous-jacent écrit automatiquement les paramètres mis à jour pour les **éléments affichés** dans les entrées de registre des catégories.  
  
  Si plusieurs VSPackages partagent une catégorie particulière, un VSPackage doit exiger que les événements soient générés lorsque les méthodes de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface sont utilisées pour modifier les paramètres de Registre stockés.  
  
  Par défaut, la génération d’événements n’est pas activée. Pour activer la génération d’événements, une catégorie doit être ouverte à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . L’IDE appelle alors la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> méthode appropriée implémentée par un VSPackage.  
  
> [!NOTE]
> Les modifications apportées à la page **de propriétés police et couleur** génèrent des événements indépendants de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Vous pouvez utiliser l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour des paramètres de police et de couleur mis en cache est nécessaire avant d’appeler les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.  
  
### <a name="storing-and-retrieving-information"></a>Stockage et récupération d’informations  
 Pour obtenir ou configurer les informations qu’un utilisateur peut modifier pour un élément d’affichage nommé dans une catégorie ouverte, les VSPackages appellent les <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> méthodes et.  
  
 Les informations sur les attributs de police pour une catégorie particulière sont obtenues à l’aide des <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> méthodes et.  
  
> [!NOTE]
> L' `fFlags` argument qui est passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode quand cette catégorie a été ouverte définit le comportement des <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> méthodes et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> . Par défaut, ces méthodes retournent uniquement des informations aboutdisplay itemsthat ont été modifiées. Toutefois, si une catégorie est ouverte à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> indicateur, les éléments d’affichage mis à jour et non modifiés sont accessibles par <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Par défaut, seules les informations sur les **éléments d’affichage** modifiés sont conservées dans le registre. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface ne peut pas être utilisée pour récupérer tous les paramètres des polices et des couleurs.  
  
> [!NOTE]
> Les <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> méthodes et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> retournent REGDB_E_KEYMISSING, (0x80040152L) lorsque vous les utilisez pour récupérer des informations sur les **éléments d’affichage**non modifiés.  
  
 Les paramètres de tous les **éléments d’affichage** d’une **catégorie** particulière peuvent être obtenus à l’aide des méthodes de l' `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interface.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implémentation de catégories personnalisées et d’éléments d’affichage](../extensibility/implementing-custom-categories-and-display-items.md)

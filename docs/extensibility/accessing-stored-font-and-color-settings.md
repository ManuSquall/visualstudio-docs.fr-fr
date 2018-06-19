---
title: L’accès à stockée paramètres de police et couleur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1280555a2b8a293fcdd0f86891a1d198ef3c99d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105790"
---
# <a name="accessing-stored-font-and-color-settings"></a>L’accès à la police stockée et les paramètres de couleur
Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) stocke les paramètres modifiés pour les polices et couleurs dans le Registre. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface pour accéder à ces paramètres.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Pour initier la persistance de l’état des polices et couleurs
 Les informations de police et de couleur sont stockées par catégorie dans l’emplacement suivant : [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], où  *\<CategoryGUID >* est le GUID de catégorie.

 Par conséquent, pour lancer la persistance, un VSPackage doit :

-   Obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface en appelant `QueryService` contre le fournisseur de services globaux.

     `QueryService` doit être appelée à l’aide d’un argument d’ID de service `SID_SVsFontAndColorStorage` et un argument d’ID d’interface `IID_IVsFontAndColorStorage`.

-   Utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode pour ouvrir une catégorie à rendre persistantes à l’aide du GUID de la catégorie et un indicateur de mode en tant qu’arguments.

     Le mode, spécifié par le `fFlags` argument, qui est construit à partir des valeurs dans le <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> énumération. Ce mode de contrôle :

    -   Les paramètres qui sont accessibles via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

    -   Tous les paramètres ou uniquement les paramètres qui modifient les utilisateurs et qui sont récupérables par le biais du <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

    -   La manière de propager les modifications apportées aux paramètres de l’utilisateur.

    -   Le format des valeurs de couleur qui sont utilisés.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Pour utiliser la persistance de l’état des polices et couleurs
 Persistance des polices et couleurs implique :

-   Synchroniser les paramètres IDE avec paramètres stockés dans le Registre.

-   Propagation des informations de modification du Registre.

-   Définition et récupération des paramètres stockés dans le Registre.

 La synchronisation du paramètre de stockage avec les paramètres de l’IDE est largement transparent. L’IDE sous-jacent écrit automatiquement les paramètres mis à jour pour **éléments affichés** pour les entrées de Registre de catégories.

 Si plusieurs packages VS partagent une catégorie particulière, un VSPackage doit exiger que les événements sont générés lorsque les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface sont utilisés pour modifier les paramètres du Registre stockée.

 Par défaut, la génération des événements n’est pas activée. Pour activer la génération des événements, une catégorie doit être ouverte à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Ouverture d’une catégorie entraîne l’IDE appeler approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> méthode qu’un VSPackage implémente.

> [!NOTE]
>  Modifications via le **police et couleur** page de propriétés générer des événements indépendants de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si une mise à jour des paramètres de police et couleur de mise en cache est nécessaire avant d’appeler les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.

### <a name="storing-and-retrieving-information"></a>Le stockage et la récupération des informations
 Pour obtenir ou configurer les informations dont un utilisateur peut modifier pour un élément d’affichage nommé dans une catégorie ouvert, VSPackages appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> méthodes.

 Pour plus d’informations sur la police des attributs pour une catégorie particulière est obtenue à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> méthodes.

> [!NOTE]
>  Le `fFlags` argument passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> méthode lors de l’ouverture de cette catégorie définit le comportement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> méthodes. Par défaut, ces méthodes retournent uniquement les informations sur les éléments d’affichage qui ont été modifiés. Toutefois, si une catégorie est ouverte à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> indicateur, les deux mises à jour et d’éléments affichés sans modification sont accessibles par <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Par défaut, seuls modifié **éléments affichés** informations sont conservées dans le Registre. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface ne peut pas être utilisé pour récupérer tous les paramètres pour les polices et couleurs.

> [!NOTE]
>  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> méthodes retournent REGDB_E_KEYMISSING, (0x80040152L) lorsque vous les utilisez pour récupérer des informations sur inchangée **afficher les éléments**.

 Les paramètres de tous les **éléments affichés** un notamment **catégorie** peuvent être obtenues en utilisant les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implémentation des catégories personnalisées et des éléments d’affichage](../extensibility/implementing-custom-categories-and-display-items.md)
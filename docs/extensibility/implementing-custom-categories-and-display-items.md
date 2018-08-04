---
title: Implémentation des catégories personnalisées et des éléments d’affichage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2dbb6744b925dac1bfa91a73024ef14ef9ad29ac
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499323"
---
# <a name="implement-custom-categories-and-display-items"></a>Implémenter des catégories personnalisées et afficher les éléments
Un VSPackage peut fournir de contrôle des polices et couleurs du texte de sa à la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) par le biais des catégories personnalisées et des éléments d’affichage.

 Catégories personnalisées et des éléments d’affichage se trouvent sur le **polices et couleurs** page de propriétés. Pour ouvrir le **polices et couleurs** page de propriété, sur le **outils** menu, cliquez sur **Options**. Développez **environnement** puis cliquez sur **polices et couleurs**.

 Lorsque vous utilisez ce mécanisme, les VSPackages doivent implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface et ses interfaces associées.

 En principe, ce mécanisme peut être utilisé pour modifier toutes les existantes **afficher les éléments** et **catégories** qui les contiennent. Toutefois, il ne doit pas être utilisée pour modifier le **texte EditorCategory** ou son **afficher les éléments**. Pour plus d’informations, consultez [vue d’ensemble de police et couleur](../extensibility/font-and-color-overview.md).

 Pour implémenter **catégories** ou **afficher les éléments**, un VSPackage doit :

-   Créez ou identifiez des catégories dans le Registre.

     Implémentation de l’IDE de le **polices et couleurs** page de propriétés utilise ces informations pour interroger correctement pour le service prenant en charge d’une catégorie donnée.

-   Créez ou identifiez les groupes (facultatifs) dans le Registre.

     Il peut être utile de définir un groupe, qui représente l’union de deux ou plusieurs catégories. Si un groupe est défini, l’IDE fusionne les sous-catégories automatiquement et distribue les éléments affichés dans le groupe.

-   Implémenter la prise en charge de l’IDE.

-   Gérer les modifications de police et de couleur.

 Pour plus d’informations, consultez [accès stockés des paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Pour créer ou identifier des catégories

-   Construire un type spécial de l’entrée de Registre de catégorie sous *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >*\FontAndColors\\ `<Category>`]*

     *\<Catégorie >* est le nom non localisé de la catégorie.

-   Remplir le Registre avec deux valeurs :

    |Name|Type|Données|Description|
    |----------|----------|----------|-----------------|
    |Category|REG_SZ|GUID|Un GUID est créé pour identifier la catégorie.|
    |Package|REG_SZ|GUID|Le GUID du service VSPackage qui prend en charge de la catégorie.|

 Le service spécifié dans le Registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> pour la catégorie correspondante.

## <a name="to-create-or-identify-groups"></a>Pour créer ou identifier des groupes

-   Construire un type spécial de l’entrée de Registre de catégorie sous *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >*\FontAndColors\\*  \<groupe >*]*

     *\<groupe >* est le nom non localisé du groupe.

-   Remplir le Registre avec deux valeurs :

    |Name|Type|Données|Description|
    |----------|----------|----------|-----------------|
    |Category|REG_SZ|GUID|Un GUID est créé pour identifier le groupe.|
    |Package|REG_SZ|GUID|Le GUID du service qui prend en charge de la catégorie.|

 Le service spécifié dans le Registre doit fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pour le groupe correspondant.

## <a name="to-implement-ide-support"></a>Pour implémenter la prise en charge de l’IDE

-   Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, qui retourne soit une <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface à l’IDE pour chaque **catégorie** ou groupe GUID fourni.

-   Pour chaque **catégorie** il prend en charge, un VSPackage implémente une instance distincte de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.

-   Les méthodes implémentées par le biais <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> doit fournir l’IDE avec :

    -   Listes de **afficher les éléments** dans le **catégorie.**

    -   Noms localisables pour **afficher les éléments**.

    -   Afficher des informations pour chaque membre de **catégorie**.

    > [!NOTE]
    >  Chaque **catégorie** doit contenir au moins un **élément d’affichage**.

-   L’IDE utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interface pour définir une union de plusieurs catégories.

     Son implémentation fournit l’IDE avec :

    -   Une liste de la **catégories** qui composent un groupe donné.

    -   Accès aux instances du <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> prenant en charge chaque **catégorie** au sein du groupe.

    -   Noms de groupe localisable.

-   Mise à jour de l’IDE :

     L’IDE met en cache les informations sur les **police et couleur** paramètres. Par conséquent, après toute modification de l’IDE **police et couleur** configuration, il est recommandé de s’assurer que le cache est à jour.

 La mise à jour le cache s’effectue via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface et peut être effectuée dans le monde entier ou seulement sélectionnées.

## <a name="to-handle-font-and-color-changes"></a>Pour gérer les modifications de police et de couleur
 Pour correctement prendre en charge la colorisation de texte qui affiche un VSPackage, le service de colorisation prenant en charge le VSPackage doit répondre aux modifications initiée par l’utilisateur apportées via la **polices et couleurs** page de propriétés. Un VSPackage pour ce faire :

-   Gestion des événements générés par l’IDE en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interface.

     L’IDE appelle la méthode appropriée suivant les modifications de l’utilisateur de la **polices et couleurs** page. Par exemple, il appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> méthode si une nouvelle police est sélectionnée.

     - ou -

-   Interrogation de l’IDE pour les modifications.

     Cela est possible via l’implémenté par le système <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface. Bien que principalement pour la prise en charge de la persistance, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> méthode peut être utilisée pour obtenir des informations de police et de couleur pour **afficher les éléments**. Pour plus d’informations, consultez [accès stockés des paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Pour garantir que les résultats obtenus par l’interrogation sont corrects, il peut être utile d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface pour déterminer si un vidage du cache et la mise à jour sont nécessaires avant d’appeler les méthodes de récupération de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Obtenir des informations de police et de couleur pour la colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Accès stockés des paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md)
- [Comment : accéder aux polices intégrées et modèle de couleurs](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Vue d’ensemble de police et de couleur](../extensibility/font-and-color-overview.md)
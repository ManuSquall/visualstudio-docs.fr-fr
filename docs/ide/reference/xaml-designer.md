---
title: Page des options du concepteur XAML | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: "1"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 459642fde4d695317a453e223edd54f223569603
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-designer-options-page"></a>Page des options du concepteur XAML
Utilisez la page des options du **concepteur XAML** pour spécifier la mise en forme des éléments et attributs dans vos documents XAML. Pour ouvrir cette page, choisissez le menu **Outils**, puis **Options**. Pour accéder à la page de propriétés du **concepteur XAML**, choisissez le nœud **Concepteur XAML**. Les paramètres du concepteur XAML sont appliqués quand vous ouvrez le document. Par conséquent, si vous modifiez les paramètres, vous devez fermer et rouvrir Visual Studio pour afficher les modifications.

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="enable-xaml-designer"></a>Activer le concepteur XAML
Ce paramètre active le concepteur XAML. Le concepteur XAML fournit une zone de travail visuelle qui vous permet de modifier des documents XAML. Certaines fonctionnalités de Visual Studio, comme IntelliSense pour les ressources et la liaison de données, nécessitent l’activation du concepteur XAML.

Les paramètres suivants s’appliquent uniquement quand le concepteur XAML est activé. Si vous modifiez cette option, vous devez redémarrer Visual Studio pour que le paramètre prenne effet.

## <a name="default-document-view"></a>Mode Document par défaut
Utilisez ce paramètre pour contrôler si le mode Design apparaît quand des documents XAML sont chargés.

|||  
|-|-|  
|**Mode Source**|Spécifie si seule la source XAML apparaît dans la vue XAML. Cela est utile quand vous chargez des documents volumineux.|  
|**Mode Design**|Spécifie si seul un concepteur visuel XAML apparaît dans la vue XAML.|  
|**Mode Fractionné**|Indique si le concepteur XAML visuel et la source XAML apparaissent l’un à côté de l’autre dans la vue XAML (emplacement basé sur le paramètre **Orientation du fractionnement**).|  

## <a name="split-orientation"></a>Orientation du fractionnement
Utilisez ce paramètre pour contrôler le moment et la façon dont le concepteur XAML s’affiche quand vous modifiez un document XAML. Ces paramètres s’appliquent uniquement quand le **Mode Document par défaut** est défini sur **Mode fractionné**.

|||  
|-|-|  
|**Vertical**|La source XAML s’affiche sur le côté gauche de la vue XAML et le concepteur XAML sur l’autre côté.|  
|**Horizontal**|Le concepteur XAML s’affiche en haut de la vue XAML et la source XAML apparaît en dessous.|  
|**Default**|Le document XAML utilise l’orientation de fractionnement recommandée pour la plateforme ciblée par le projet du document. Pour la plupart des plateformes, il s’agit de **Horizontal**.|  

## <a name="zoom-by-using"></a>Zoomer en utilisant
Utilisez ce paramètre pour déterminer le fonctionnement du zoom pendant la modification d’un document XAML.

|||  
|-|-|  
|**Roulette de la souris**|Effectuez un zoom avant dans le concepteur XAML en faisant tourner la roulette de la souris.|  
|**Ctrl + roulette de la souris**|Effectuez un zoom avant dans le concepteur XAML en appuyant sur la touche Ctrl tout en faisant tourner la roulette de la souris.|  
|**Alt + roulette de la souris**|Effectuez un zoom avant dans le concepteur XAML en appuyant sur la touche Alt tout en faisant tourner la roulette de la souris.|  

Ces paramètres déterminent le comportement du concepteur pendant la modification d’un document XAML.

|||  
|-|-|  
|**Nommer automatiquement les éléments interactifs à la création**|Spécifie si un nom par défaut est fourni pour un nouvel élément interactif quand vous l’ajoutez au concepteur.|  
|**Insérer automatiquement des propriétés de disposition après la création d’éléments**|Spécifie si des propriétés de disposition sont fournies pour un nouvel élément quand vous l’ajoutez au concepteur.|  
|**Utiliser une disposition basée sur un quadrant**|Indique si le contrôle sélectionné s’aligne sur les bords les plus proches du conteneur parent. Si cette case est décochée, l’alignement des contrôles ne change pas pendant une opération de déplacement ou de création.|  
|**Remplir automatiquement les éléments de la boîte à outils**|Spécifie si les contrôles utilisateur et les contrôles personnalisés dans la solution actuelle sont automatiquement affichés dans la boîte à outils.|  

## <a name="settings-blend-only"></a>Paramètres (Blend uniquement)
Utilisez ces options pour déterminer des paramètres pendant de la modification de fichiers XAML à l’aide de Blend.

|||  
|-|-|  
|**Zoomer en utilisant**|Effectuez un zoom avant dans le concepteur XAML en faisant tourner la roulette de la souris, ou en appuyant sur la touche Ctrl ou Alt tout en faisant tourner la roulette de la souris.|  
|**Unités de type**|Spécifie si les mesures dans le concepteur sont basées sur des points ou des pixels. Comme les applications Windows universelles ne prennent pas en charge les points, les unités sont automatiquement converties en pixels si l’option **Points** est sélectionnée.|  

## <a name="artboard-blend-only"></a>Planche graphique (Blend uniquement)
Utilisez ces paramètres pour déterminer le comportement du concepteur XAML pendant la modification de documents XAML dans Blend.

### <a name="snapping"></a>Accrochage

|||  
|-|-|  
|**Afficher la grille d’accrochage**|Quand cette option est sélectionnée, le quadrillage apparaît dans le concepteur pour vous aider à aligner les contrôles. Les contrôles ajoutés dans le concepteur s’accrochent au quadrillage quand l’option **Accrocher sur le quadrillage** est sélectionnée.|  
|**Accrocher sur le quadrillage**|Quand vous ajoutez ou déplacez des contrôles dans le concepteur, ils s’accrochent sur le quadrillage.|  
|**Espacement du quadrillage**|Spécifie l’espacement du quadrillage en pixels ou en points (comme déterminé par le paramètre **Unités de type**).|  
|**Accrocher sur les lignes d’accrochage**|Spécifie si les contrôles s’accrochent sur les lignes d’accrochage.|  
|**Marge par défaut**|Quand l’option **Accrocher sur les lignes d’accrochage** est activée, spécifie l’espacement entre le contrôle et les lignes d’accrochage en pixels ou en points (comme déterminé par le paramètre **Unités de type**).|  
|**Marge intérieure par défaut**|Quand l’option **Accrocher sur les lignes d’accrochage** est activée, spécifie l’espacement supplémentaire entre le contrôle et les lignes d’accrochage en pixels ou en points (comme déterminé par le paramètre **Unités de type**).|  

### <a name="animation"></a>Animation
Utilisez ce paramètre pour déterminer si un avertissement s’affiche quand des animations dépendantes (non accélérées) sont activées dans Blend.

### <a name="effects"></a>Effects (Effets)
Utilisez ces paramètres pour déterminer si des effets sont affichés pendant la modification de fichiers XAML dans le concepteur XAML à l’aide de Blend.

|||  
|-|-|  
|**Prévisualiser les effets**|Spécifie si les effets sont affichés pendant la modification de fichiers XAML dans le concepteur XAML à l’aide de Blend.|  
|**Seuil du zoom**|Spécifie le pourcentage de zoom pour l’affichage des effets quand la case **Prévisualiser les effets** est cochée. Si vous effectuez un zoom au-delà de ce paramètre, les effets ne sont plus affichés dans le concepteur XAML.|  

## <a name="see-also"></a>Voir aussi  
 [Intégration du format XAML au format WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [Guide pratique pour modifier les paramètres de vue XAML](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Procédures pas à pas pour XAML et le code](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)

---
title: "Modifier le style des objets dans Blend | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Modifier le style des objets dans Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le moyen le plus simple de personnaliser un objet est d'en définir les propriétés dans le panneau **Propriétés**.  
  
 Si vous voulez réutiliser des paramètres ou des groupes de paramètres, créez une ressource réutilisable.  Il peut s'agir d'un *style*, d'un *modèle* ou de quelque chose de simple comme une couleur personnalisée.  Vous pouvez aussi faire en sorte qu'un contrôle change d'apparence en fonction de son état,  par exemple, un bouton qui devient vert quand l'utilisateur clique dessus.  
  
 **Dans cette rubrique** :  
  
-   [Pinceaux : modifier l'apparence d'un objet](#Brushes)  
  
-   [Styles et modèles : créer une apparence cohérente pour les contrôles](#Styles)  
  
-   [États visuels : modifier l'apparence d'un contrôle en fonction de son état](#Visual)  
  
-   [Ressources : créer des couleurs, des styles et des modèles et les réutiliser ultérieurement](#Resources)  
  
##  <a name="Brushes"></a> Pinceaux : modifier l'apparence d'un objet  
 Appliquez un pinceau à un objet si vous voulez modifier son apparence.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Éditeur de pinceaux](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### Peindre une image ou un motif qui se répète sur un objet  
 Vous pouvez peindre une image ou un motif qui se répète sur un objet à l'aide d'un *pinceau de mosaïque*.  
  
 Pour créer un pinceau de mosaïque, commencez par créer une ressource de *pinceau d'image*, de *pinceau de dessin* ou de *pinceau visuel*.  
  
 Vous pouvez créer un pinceau d'image à l'aide d'une image.  Les illustrations suivantes montrent le pinceau d'image, le pinceau d'image en mosaïque et le pinceau d'image retourné.  
  
 Vous pouvez créer un pinceau de dessin à l'aide d'un dessin vectoriel, tel qu'un trait ou une forme.  Les illustrations suivantes montrent le pinceau de dessin, le pinceau de dessin en mosaïque et le pinceau de dessin retourné.  
  
 Vous pouvez créer un pinceau visuel à partir d'un contrôle, tel qu'un bouton.  Les illustrations suivantes montrent le pinceau visuel et le pinceau visuel en mosaïque.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Pinceaux de mosaïque](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Styles et modèles : créer une apparence cohérente pour les contrôles  
 Vous pouvez concevoir l'apparence et le comportement d'un même contrôle et appliquer cette conception à d'autres contrôles pour vous éviter d'avoir à les gérer un à un.  
  
 **Avez\-vous intérêt à utiliser un style ?** Si vous voulez simplement définir des propriétés par défaut \(comme la couleur d'un bouton\), utilisez un *style*.  Vous pouvez modifier un contrôle même après lui avoir appliqué un style.  
  
 **Avez\-vous intérêt à utiliser un modèle ?** Si vous voulez modifier la structure d'un contrôle, utilisez un *modèle*.  Si vous envisagez de convertir un graphique ou un logo en bouton,  sachez que vous ne pouvez pas modifier un contrôle après lui avoir appliqué un modèle.  
  
### Créer un modèle ou un style  
 Il existe deux façons de créer un modèle.  Vous pouvez soit convertir un objet de la planche graphique en contrôle, soit baser votre modèle sur un contrôle existant.  
  
 Pour convertir un objet en modèle de contrôle, sélectionnez l'objet puis, dans le menu **Outils**, choisissez **Créer un contrôle**.  
  
 Si vous voulez baser votre modèle sur un contrôle existant, sélectionnez un objet sur la planche graphique.  Ensuite, en haut de la planche graphique, choisissez successivement le bouton de la barre de navigation, **Modifier le modèle**, puis **Modifier une copie** ou **Créer vide**.  
  
 Pour créer un style, sélectionnez l'objet puis, dans le menu **Objet**, choisissez **Modifier le style**, puis **Modifier une copie** ou **Créer vide**.  
  
-   Choisissez **Modifier une copie** pour commencer avec le style ou le modèle par défaut du contrôle.  
  
-   Choisissez **Créer vide** pour commencer à zéro.  
  
 L'option **Modifier actuel** s'affiche uniquement si vous modifiez un style ou un modèle que vous avez déjà créé.  Elle ne s'affiche pas pour un contrôle qui utilise toujours un modèle système par défaut.  
  
 Dans la boîte de dialogue **Créer une ressource de style**, vous pouvez soit nommer le style ou le modèle pour pouvoir l'utiliser ultérieurement, soit appliquer le style ou le modèle à tous les contrôles de ce type.  
  
> [!NOTE]
>  Vous ne pouvez pas créer de styles ou de modèles pour chaque type de contrôle.  Si un contrôle ne les prend pas en charge, le bouton de la barre de navigation ne s'affiche pas au\-dessus de la planche graphique.  
>   
>  Pour revenir à la portée d'édition de votre document principal, cliquez sur **Rétablir l'étendue à** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b").  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Créer un style](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Création d'un modèle de contrôle dans Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### Appliquer un style ou un modèle à un contrôle  
 Cliquez avec le bouton droit sur un objet dans le panneau [Objets et chronologie](http://msdn.microsoft.com/fr-fr/135a5a5e-ec6d-4f38-8827-60e284cd5f57), choisissez **Modifier un modèle**, puis **Appliquer la ressource**.  
  
### Restaurer le style ou le modèle par défaut d'un contrôle  
 Sélectionnez le contrôle puis, dans le panneau [Propriétés](http://msdn.microsoft.com/fr-fr/135a5a5e-ec6d-4f38-8827-60e284cd5f57), recherchez la propriété **Style** ou **Modèle**.  Cliquez ensuite sur **Options avancées** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb"), puis sur **Réinitialiser** dans le menu contextuel.  
  
##  <a name="Visual"></a> États visuels : modifier l'apparence d'un contrôle en fonction de son état  
 Les contrôles peuvent avoir des apparences visuelles différentes en fonction des interactions de l'utilisateur.  Par exemple, vous pouvez faire en sorte qu'un bouton devienne vert quand un utilisateur clique dessus ou qu'il exécute une animation.  Vous pouvez raccourcir ou allonger la durée entre les états visuels à l'aide de transitions.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Gérer l'état de vos contrôles WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Ressources : créer des couleurs, des styles et des modèles et les réutiliser ultérieurement  
 Vous pouvez convertir pratiquement tous les éléments de votre projet en ressource.  Une ressource consiste simplement en un objet que vous pouvez réutiliser à différents endroits dans votre application.  Par exemple, vous pouvez créer une couleur, en faire une ressource, puis appliquer cette couleur à plusieurs objets.  Pour modifier la couleur de tous ces objets, il vous suffit de modifier la ressource de couleur.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Une bref exposé sur les ressources](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## Voir aussi  
 [Création d'une interface utilisateur à l'aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
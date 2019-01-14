---
title: Modifier le style des objets dans Blend
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cd8b8d9b3f9a12fa69cf708b0f7a3b16bae83d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906785"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modifier le style des objets dans Blend

Le moyen le plus simple de personnaliser un objet est d’en définir les propriétés dans le panneau **Propriétés**.

Si vous voulez réutiliser des paramètres ou des groupes de paramètres, créez une ressource réutilisable. Il peut s’agir d’un *style*, d’un *modèle* ou de quelque chose de simple comme une couleur personnalisée. Vous pouvez aussi faire en sorte qu'un contrôle change d'apparence en fonction de son état, par exemple, un bouton qui devient vert quand l'utilisateur clique dessus.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pinceaux : modifier l’apparence d’un objet

Appliquez un pinceau à un objet si vous voulez modifier son apparence.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Peindre une image ou un motif qui se répète sur un objet

Vous pouvez peindre une image ou un motif qui se répète sur un objet à l’aide d’un *pinceau mosaïque*.

Pour créer un pinceau mosaïque, commencez par créer une ressource de *pinceau image*, de *pinceau de dessin* ou de *pinceau visuel*.

Vous pouvez créer un pinceau d'image à l'aide d'une image. Les illustrations suivantes montrent le pinceau d'image, le pinceau d'image en mosaïque et le pinceau d'image retourné.

![Pinceau image](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Pinceau image en mosaïque](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Pinceau image retourné](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Vous pouvez créer un pinceau de dessin à l'aide d'un dessin vectoriel, tel qu'un trait ou une forme. Les illustrations suivantes montrent le pinceau de dessin, le pinceau de dessin en mosaïque et le pinceau de dessin retourné.

![Pinceau de dessin](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Pinceau de dessin en mosaïque](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Pinceau de dessin retourné](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Vous pouvez créer un pinceau visuel à partir d'un contrôle, tel qu'un bouton. Les illustrations suivantes montrent le pinceau visuel et le pinceau visuel en mosaïque.

![Pinceau visuel](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Pinceau visuel en mosaïque](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Styles et modèles : créer une apparence cohérente parmi les contrôles

Vous pouvez concevoir l’apparence et le comportement d’un même contrôle et appliquer cette conception à d’autres contrôles pour vous éviter d’avoir à les gérer un à un.

**Avez-vous intérêt à utiliser un style ?**  : si vous voulez simplement définir des propriétés par défaut (comme la couleur d’un bouton), utilisez un *style*. Vous pouvez modifier un contrôle même après lui avoir appliqué un style.

**Avez-vous intérêt à utiliser un modèle ?**  : si vous voulez changer la structure d’un contrôle, utilisez un *modèle*. Si vous envisagez de convertir un graphique ou un logo en bouton, sachez que vous ne pouvez pas modifier un contrôle après lui avoir appliqué un modèle.

### <a name="create-a-template-or-style"></a>Créer un modèle ou un style

Vous pouvez créer un modèle de deux façons. Vous pouvez soit convertir un objet de la planche graphique en contrôle, soit baser votre modèle sur un contrôle existant.

Pour convertir un objet en modèle de contrôle, sélectionnez l’objet puis, dans le menu **Outils**, choisissez **Créer un contrôle**.

Si vous voulez baser votre modèle sur un contrôle existant, sélectionnez un objet sur la planche graphique. Ensuite, en haut de la planche graphique, choisissez successivement le bouton de la barre de navigation, **Modifier le modèle**, puis **Modifier une copie** ou **Créer vide**.

![Menu Modifier un modèle](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Pour créer un style, sélectionnez l’objet puis, dans le menu **Objet**, choisissez **Modifier le style**, puis **Modifier une copie** ou **Créer vide**.

- Choisissez **Modifier une copie** pour commencer avec le style ou le modèle par défaut du contrôle.

- Choisissez **Créer vide** pour commencer à zéro.

L’option **Modifier actuel** s’affiche uniquement si vous modifiez un style ou un modèle que vous avez déjà créé. Elle ne s’affiche pas pour un contrôle qui utilise toujours un modèle système par défaut.

Dans la boîte de dialogue **Créer une ressource de style**, vous pouvez soit nommer le style ou le modèle pour pouvoir l’utiliser ultérieurement, soit appliquer le style ou le modèle à tous les contrôles de ce type.

![Boîte de dialogue Créer une ressource de style](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Vous ne pouvez pas créer de styles ou de modèles pour chaque type de contrôle. Si un contrôle ne les prend pas en charge, le bouton de la barre de navigation ne s’affiche pas au-dessus de la planche graphique.
> Pour revenir à l’étendue d’édition de votre document principal, cliquez sur **Rétablir l’étendue à** ![Icône Rétablir l’étendue à](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Appliquer un style ou un modèle à un contrôle

Cliquez avec le bouton droit sur un objet dans le panneau [Objets et chronologie](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel), choisissez **Modifier un modèle**, puis **Appliquer la ressource**.

![Menu Appliquer la ressource](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Restaurer le style ou le modèle par défaut d'un contrôle

Sélectionnez le contrôle puis, dans le panneau [Propriétés](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel), recherchez la propriété **Style** ou **Modèle**. Sélectionnez **Options avancées**, puis cliquez sur **Réinitialiser** dans le menu contextuel.

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>États visuels : modifier l’apparence d’un contrôle en fonction de son état

Les contrôles peuvent avoir des apparences visuelles différentes en fonction des interactions de l'utilisateur. Par exemple, vous pouvez faire en sorte qu'un bouton devienne vert quand un utilisateur clique dessus ou vous pouvez exécuter une animation. Vous pouvez raccourcir ou allonger la durée entre les états visuels à l'aide de transitions.

![État de pointage avec la souris](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Regardez une courte vidéo :** ![Bouton Lecture](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Gérer l’état de vos contrôles WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Ressources : créer des couleurs, des styles et des modèles, et les réutiliser ultérieurement

Vous pouvez convertir pratiquement tous les éléments de votre projet en ressource. Une ressource consiste simplement en un objet que vous pouvez réutiliser à différents endroits dans votre application. Par exemple, vous pouvez créer une couleur, en faire une ressource, puis appliquer cette couleur à plusieurs objets. Pour modifier la couleur de tous ces objets, il vous suffit de modifier la ressource de couleur.

![Bouton Convertir la couleur en ressource](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Boîte de dialogue Créer une ressource de couleur](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Voir aussi

- [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
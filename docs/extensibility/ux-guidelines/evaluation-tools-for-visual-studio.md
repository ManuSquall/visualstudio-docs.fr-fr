---
title: Outils d’évaluation pour Visual Studio | Microsoft Docs
description: Utilisez cette liste de vérification pour évaluer la qualité de l’expérience utilisateur pour les détails visuels et d’interaction pour les nouvelles fonctionnalités que vous concevez pour Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baee9f3e2eaefcd659f8428bd566711949d0fe90
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900757"
---
# <a name="evaluation-tools-for-visual-studio"></a>Outils d’évaluation pour Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Liste de vérification de l’artisan pour Visual Studio
 Utilisez cette liste de vérification pour évaluer la qualité de l’expérience utilisateur pour les détails visuels et d’interaction.

### <a name="overview"></a>Vue d’ensemble

- Vérifiez que toutes les commandes génèrent des commentaires qui indiquent aux utilisateurs que leurs commandes ont été exécutées.

- Vérifiez que tous les éléments et contrôles d’interface utilisateur sont visibles dans tous les thèmes et en mode contraste élevé.

- Vérifiez que les sélections inactives et actives sont toujours différenciées, en mode standard et en mode contraste élevé.

- Vérifiez que le focus est toujours visible et apparent.

### <a name="performance"></a>Performances

- Vérifiez qu’un type d’indicateur « occupé » est affiché si une commande prend plus d’une seconde.

- Vérifiez que si une commande prend plus de 10 secondes pour s’exécuter, une barre de progression explicite, determine (par défaut) ou indéterminée, s’affiche.

### <a name="ui-text"></a>Texte de l’interface utilisateur

- Vérifiez que toutes les étiquettes sont de phrase ou de titre et qu’aucun texte n’est entièrement en minuscules.

    ||Correct.|Incorrect.|
    |-|-------------|---------------|
    |**Texte de la commande (tout)**|Casse de la phrase :<br /><br /> **Nom du répertoire :**|Nom du répertoire :|
    |**Texte du bouton (client)**|Casse du titre :<br /><br /> **[Défini par défaut]**|DÉFINIR PAR DÉFAUT|
    |**Texte du bouton (en ligne)**|Casse de la phrase :<br /><br /> **[Défini par défaut]**||

- Vérifiez que toutes les étiquettes, à l’exception des en-têtes de groupe et des boutons, se terminent par un signe deux-points et précèdent le contrôle avec lequel ils sont couplés.

- Vérifiez que des boutons, des commandes et des liens de commande lançant l’interface utilisateur pour capturer l’entrée utilisateur se terminent par des points de suspension **[...]**.

  Exemples :

  - Un bouton **[avancé...]** sur une boîte de dialogue.

  - Les options de commande du menu Outils (**options > des outils**) ne doivent pas recevoir de points de suspension, car le lancement de la boîte de dialogue elle-même est l’objectif de la commande.

- Vérifiez que l’interface utilisateur ne contient pas d’abréviations, sauf pour les termes standard du secteur. Par exemple, ni le code HTML, ni le protocole TCP/IP ne doivent être orthographiés, bien que insuffisance (mémoire insuffisante) et les informations d’identification personnelle.

### <a name="keyboard-access"></a>Accès par le clavier

- Vérifiez qu’il existe un moyen d’accomplir chaque tâche à l’aide du clavier. En général, cela s’effectue par le biais de l’accès au clavier pour chaque contrôle, mais pour certaines zones très visuelles, une solution de contournement telle que le passage en mode code est acceptable.

- Vérifiez que vous pouvez parcourir les contrôles dans un ordre logique (de gauche à droite et de haut en bas). Bien qu’il s’agit d’une meilleure pratique pour la plupart des contrôles, tous les contrôles n’ont pas besoin de cette approche. Par exemple, vérifiez que les contrôles de case d’option se trouvent dans un groupe avec un seul taquet de tabulation.

- Vérifiez que tous les contrôles ont des étiquettes et que chaque étiquette a un mnémonique (les exceptions incluent des contrôles non étiquetés qui peuvent suivre un contrôle étiqueté dans l’onglet).

- Vérifiez qu’il n’y a pas de conflits mnémoniques.

### <a name="fonts"></a>Polices

- Vérifiez que toutes les polices (face, taille, couleur) sont utilisées de manière cohérente et gèrent la hiérarchie.

- Vérifiez que tous les éléments d’interface utilisateur utilisent le service de police d’environnement. (Voir [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pour vérifier si le service est en cours d’utilisation, accédez à **outils > Options > polices et couleurs**. Dans la liste déroulante paramètres, choisissez police d’environnement et remplacez le type de police par un style différent (par exemple, Harrington ou Comic sans) et définissez la taille sur 12 pt. Puis cliquez sur OK. Vous devrez peut-être redémarrer l’IDE, mais la plupart des interfaces utilisateur seront immédiatement modifiées. Les zones qui ne récupèrent pas le changement de police même au redémarrage n’utilisent pas la police d’environnement.

- Vérifiez que les polices dérivées du service (par exemple, texte en gras ou agrandi) conservent leur taille et leur mise en forme par rapport au texte « normal » lorsque la taille de police de l’environnement est modifiée.

- Vérifiez qu’il n’y a pas de bogues de découpage en raison des polices agrandies. Les polices découpées sont probablement le résultat de contrôles de hauteur fixe ou de conteneurs de hauteur fixe.

### <a name="dialogs"></a>Boîtes de dialogue

- Vérifiez que le titre de la boîte de dialogue est le même que celui de la commande qui l’a lancée.

- Vérifiez que tous les contrôles standard sont cohérents avec le système d’exploitation : la couleur d’arrière-plan est standard et aucun contrôle ne doit avoir un style remodèle spécial qui les fait apparaître différemment des contrôles standard.

- Vérifiez que les marges dans le formulaire doivent être de 12 pixels et qu’elles doivent apparaître uniformes et cohérentes.

- Vérifiez que les boîtes de dialogue sont centrées dans l’interpréteur de commandes IDE ou dans la fenêtre qui les a générées.

- Lorsque cela s’avère utile, les boîtes de dialogue doivent être redimensionnables. Pour les boîtes de dialogue redimensionnables, vérifiez que lors du redimensionnement, les contrôles appropriés doivent être redimensionnés alors que d’autres parties de la boîte de dialogue restent constantes.

- Vérifiez que les boîtes de dialogue redimensionnables conservent toute taille ajustée par l’utilisateur (taille, emplacement, expansion des contrôles de boîte de dialogue, etc.).

- Vérifiez qu’il n’y a pas d’icône dans la barre de titre.

- Vérifiez qu’il n’y a pas de boutons réduire et agrandir dans la barre de titre.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Boutons d’opération de la boîte de dialogue (client VS uniquement)

- Vérifiez que les boutons d’opération sont dans cet ordre : **OK**, **Annuler**, **appliquer**.

- Vérifiez que les boutons **OK** et **Annuler** sont la taille standard : 75x23 pixels.

- Vérifiez que les boutons **OK** et **Annuler** sont de taille égale, quelle que soit la longueur de la chaîne.

- Si l’étiquette d’un bouton d’opération requiert que le bouton soit plus grand que le bouton standard, vérifiez que le bouton **Annuler** correspondant est de taille égale.

- Vérifiez qu’il y a un remplissage de 6 pixels entre les boutons et les contrôles associés.

- Vérifiez que les boutons **OK** et **Annuler** n’ont pas de mnémoniques (touches d’accès définies par une lettre soulignée).

- Vérifiez qu’un bouton (généralement **OK**) a le focus par défaut.

- Vérifiez que la **touche Échap** annule la boîte de dialogue

- Vérifiez que la touche **entrée** exécute le bouton par défaut si le focus n’est pas dans un contrôle qui traite l’entrée.

- Vérifiez que les boutons **OK** et **Annuler** sont positionnés dans le coin inférieur droit de la boîte de dialogue. Dans de rares exceptions, il est acceptable qu’elles soient empilées verticalement dans le coin supérieur droit.

- Vérifiez que la configuration verticale est utilisée uniquement si d’autres boutons sont alignés horizontalement dans la boîte de dialogue.

### <a name="control-standards"></a>Normes de contrôle

#### <a name="general"></a>Général

- Vérifiez que, dans la mesure du possible, il existe de bonnes valeurs par défaut pour accélérer l’interaction de l’utilisateur et diriger les utilisateurs vers un résultat sécurisé ou commun.

- Vérifiez que les contrôles standard se comportent de la même façon afin que les utilisateurs sachent ce qui se passe en fonction de l’expérience précédente.

#### <a name="label-controls"></a>Contrôles Label

- Vérifiez que chaque contrôle a une étiquette et que chaque étiquette est associée visuellement à son contrôle (généralement dans une plage de 4-6 pixels) et est plus proche de son contrôle correspondant à d’autres contrôles.

- Vérifiez que les étiquettes sont positionnées à gauche avec le bord gauche du contrôle s’ils sont positionnés au-dessus et qu’ils sont centrés horizontalement, afin que la ligne de base de l’étiquette soit alignée sur la ligne de base du texte d’entrée, si elle est positionnée à gauche.

- Vérifiez que si plusieurs contrôles d’entrée et d’étiquette empilés sont positionnés à gauche d’un contrôle, les étiquettes sont alignées à gauche et une distance égale à partir du bord de la boîte de dialogue, ne sont jamais alignées vers la droite et une distance égale à partir des contrôles. Les paires doivent être distribuées uniformément, sauf si elles ont besoin d’espace supplémentaire pour indiquer le regroupement.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Contrôles d’entrée (zones de texte et zones de liste déroulante)

- Vérifiez que lorsque vous utilisez la police d’environnement par défaut, la hauteur d’affichage pour les zones de texte, les zones de liste déroulante et les boutons sont les 23 pixels.

- Si le texte d’indication est utilisé, vérifiez que la couleur est définie sur `Environment.ControlEditHintText` à l’aide du service de couleurs.

- Si le champ est un champ obligatoire qui doit être identifié comme tel, vérifiez les éléments suivants :

  - que l’arrière-plan a la valeur `Environment.ControlEditRequiredBackground` et que le premier plan a la valeur `Environment.ControlEditRequiredHintText`

  - qu’il existe un texte d’indication dans le contrôle qui s’affiche sous la forme **« \<Required> »**

#### <a name="button-controls"></a>Contrôles boutons

- Vérifiez que les boutons ont une taille minimale de 75x23 pixels, sauf s’ils s’adaptent à du texte plus long.

- Vérifiez que les boutons ont des marges gauche et droite de 3-5 pixels, ainsi que le remplissage du contenu.

- Il est possible d’utiliser un petit bouton carré avec des points de suspension **[...]** à la place d’un bouton **[Parcourir...]** (ou d’une fonctionnalité similaire). S’il est utilisé, vérifiez que la taille du bouton est 23x23.

- S’il existe plus d’un bouton **[Parcourir.** ..] dans une boîte de dialogue, vérifiez que la version abrégée (points de suspension uniquement **[...]**) est utilisée pour tous les.

- Vérifiez que les boutons de sélection **[...]** n’ont pas de mnémonique. Lorsque le focus se trouve sur le contrôle d’entrée en regard de celui-ci, un onglet doit déplacer le focus sur le bouton de sélection.

- Vérifiez que les boutons, commandes et liens de commande qui lancent une interface utilisateur secondaire qui capturent davantage d’entrées utilisateur doivent se terminer par des points de suspension **[...]**.

#### <a name="hyperlinks"></a>Liens hypertexte

- Vérifiez qu’un contrôle de lien hypertexte ne clignote jamais en rouge lorsqu’il est actif. Il s’agit d’un indicateur indiquant que le service de couleurs n’est pas utilisé

- Vérifiez que les couleurs VS utilisées sont :

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Vérifiez que les liens hypertexte s’affichent en bleu sans trait de soulignement, sauf s’ils sont incorporés dans un paragraphe.

#### <a name="check-boxes"></a>Cases à cocher

- Si une case à cocher contient du texte à plusieurs lignes, vérifiez que la zone s’aligne sur la première ligne de texte, et non centrée verticalement sur toutes les lignes.

- Vérifiez que les cases à cocher indiquent toujours un choix binaire et que vous ne parvenez pas à accéder à l’utilisateur ou à ouvrir de nouvelles fenêtres ou pages.

- Si une case à cocher présente une option associée à un contrôle d’entrée, vérifiez qu’elle est positionnée sur le côté gauche et très proche sous ce contrôle pour indiquer sa relation.

- Vérifiez qu’une case à cocher n’est **jamais** utilisée pour activer l’ensemble du contenu d’une boîte de dialogue ou d’une page.

#### <a name="group-boxes"></a>Zones de groupe

- Vérifiez qu’une boîte de dialogue ne contient pas une seule zone de groupe dans celle-ci, qui contient la totalité du contenu de la boîte de dialogue.

- Vérifiez qu’il y a au moins deux contrôles dans chaque zone de groupe.

- Il est rare qu’il y ait plus de deux zones de groupe dans une boîte de dialogue.

- Vérifiez qu’il n’y a aucune zone de groupe imbriquée.

### <a name="icons"></a>Icônes

- Vérifiez que les icônes apparaissent correctement inversées dans le thème sombre.

- Vérifiez que toutes les icônes sont basées sur les concepts fondamentaux.

- Vérifiez que chaque icône est distincte, facile à reconnaître et ne contient pas plus de deux concepts (sans modificateur d’État/langage).

- Vérifiez que l’icône de base apparaît centrée dans l’espace.

- Vérifiez que toutes les icônes apparaissent lisibles en mode contraste élevé.

- Vérifiez que toutes les couleurs utilisées s’alignent sur les normes d’utilisation des couleurs.

- Vérifiez qu’il n’y a pas de Halo (bordures) autour des icônes. (S’il est présent, le Halo doit correspondre à la couleur d’arrière-plan de l’interface utilisateur adjacente).

### <a name="touch-enabled-ui"></a>INTERFACE tactile

- Vérifier que les contrôles interactifs sont suffisamment grands pour être facilement touchable-taille minimale de **23x23 pixels**

- Vérifiez que la taille des contrôles les plus fréquemment utilisés est d’au moins **40 x 40 pixels** .

- Vérifier que les contrôles interactifs disposent d’au moins **5 pixels d’espacement** entre eux

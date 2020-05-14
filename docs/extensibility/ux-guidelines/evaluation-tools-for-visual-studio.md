---
title: Outils d’évaluation pour Visual Studio (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698429"
---
# <a name="evaluation-tools-for-visual-studio"></a>Outils d’évaluation pour Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Liste de contrôle de l’artisanat pour Visual Studio
 Utilisez cette liste de contrôle pour évaluer la qualité de l’expérience utilisateur pour les détails visuels et d’interaction.

### <a name="overview"></a>Vue d'ensemble

- Vérifiez que toutes les commandes donnent lieu à des commentaires qui indiquent aux utilisateurs que leurs commandes ont été effectuées.

- Vérifiez que tous les éléments et contrôles de l’interface utilisateur sont visibles dans tous les thèmes et en mode contraste élevé.

- Vérifiez que la sélection inactive et active est toujours différenciée, tant en mode standard que en mode contraste élevé.

- Vérifiez que l’accent est toujours visible et apparent.

### <a name="performance"></a>Performances

- Vérifiez qu’une sorte d’indicateur « occupé » est affiché si une commande prend plus d’une seconde pour terminer.

- Vérifiez que si une commande prend plus de 10 secondes à remplir, une barre de progression explicite, déterminée (préférée) ou indéterminée, est affichée.

### <a name="ui-text"></a>Texte de l’interface utilisateur

- Vérifiez que toutes les étiquettes sont des cas de phrase ou de titre et qu’aucun texte n’est entièrement inférieur.

    ||Correct|Incorrect|
    |-|-------------|---------------|
    |**Texte de commande (tous)**|Cas de peine :<br /><br /> **Nom de l’annuaire:**|Nom de l’annuaire:|
    |**Texte bouton (client)**|Cas de titre:<br /><br /> **[ Définir comme par défaut ]**|DÉFINI COMME PAR DÉFAUT|
    |**Texte bouton (en ligne)**|Cas de peine :<br /><br /> **[ Définir comme par défaut ]**||

- Vérifiez que toutes les étiquettes, à l’exception des en-têtes et des boutons de groupe, se terminent par un côlon et précèdent le contrôle avec lequel ils sont appariés.

- Vérifiez que les boutons, les commandes et les liens de commande qui lancent l’interface utilisateur pour capturer l’entrée de l’utilisateur se terminent dans une ellipsis **[...]**.

  Exemples :

  - Un bouton **[avancé...]** sur un dialogue.

  - Les options de commande dans le cadre du menu Tools **(Outils > Options**) ne devraient pas obtenir une ellipsis, car le lancement du dialogue lui-même est l’intention de la commande.

- Vérifiez que l’interface utilisateur ne contient aucune abréviation, à l’exception des conditions standard de l’industrie. Par exemple, ni HTML, ni TCP/IP n’ont besoin d’être précisés, bien que l’OOM (hors mémoire) et piI (informations personnellement identifiables) devraient.

### <a name="keyboard-access"></a>Accès par le clavier

- Vérifiez qu’il existe un moyen d’accomplir chaque tâche avec le clavier. Généralement, cela est accompli grâce à l’accès au clavier pour chaque contrôle, mais pour certains domaines très visuels, une solution de contournement comme aller à la vue de code est acceptable.

- Vérifiez que vous pouvez ongletr à travers les contrôles dans un ordre logique (de gauche à droite et de haut en bas). Bien qu’il s’agisse d’une pratique exemplaire pour la plupart des contrôles, tous les contrôles n’exigent pas cette approche. Par exemple, vérifiez que les commandes de boutons radio sont dans un groupe avec un seul arrêt d’onglet.

- Vérifiez que tous les contrôles ont des étiquettes et que chaque étiquette a un mnémonique (les exceptions incluent certains contrôles non étiquetés qui pourraient suivre un contrôle étiqueté dans l’onglet).

- Vérifiez qu’il n’y a pas de conflits mnémoniques.

### <a name="fonts"></a>Polices

- Vérifiez que toutes les polices (visage, taille, couleur) sont utilisées de façon cohérente et maintenez la hiérarchie.

- Vérifiez que tous les éléments d’interface utilisateur utilisent le service de police de l’environnement. (Voir [Fonts et Formatting pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pour vérifier si le service est utilisé, rendez-vous sur **Tools > Options > Fonts and Colors**. Dans le dropdown Paramètres, choisissez Environment Font et changer le visage de police à quelque chose de stylistiquement différent (comme Harrington ou Comic Sans) et définir la taille à 12 pt. Puis cliquez sur OK. Vous devrez peut-être redémarrer l’IDE, mais la plupart des interfaces utilisateur changeront immédiatement. Les zones qui ne captent pas le changement de police, même sur le redémarrage, n’utilisent pas la police de l’environnement.

- Vérifiez que les polices dérivées du service (par exemple, le texte gras ou agrandi) conservent leur taille et leur formatage par rapport au texte « normal » lorsque la taille de la police de l’environnement est modifiée.

- Vérifiez qu’il n’y a pas de bogues de coupure dus aux polices agrandies. Les polices qui sont coupées sont probablement le résultat de commandes de hauteur fixe ou de conteneurs à hauteur fixe.

### <a name="dialogs"></a>Boîtes de dialogue

- Vérifiez que le titre de dialogue est le même que la commande qui l’a lancé.

- Vérifiez que tous les contrôles standard sont compatibles avec le système d’exploitation : la couleur de fond est standard et aucun contrôle ne devrait avoir un style re-templated spécial qui les rend différents des contrôles standard.

- Vérifiez que les marges dans le formulaire doivent être de 12 pixels et doivent apparaître uniformes et cohérentes.

- Vérifiez que les dialogues semblent centrés dans la coquille IDE ou la fenêtre qui les a frayé.

- Lorsqu’ils sont utiles, les dialogues doivent être résizables. Pour les dialogues qui sont resizables, vérifiez qu’une fois ressizing, les contrôles appropriés doivent se resize tandis que d’autres parties du dialogue restent constantes.

- Vérifiez que les dialogues résizables persistent toute taille ajustée par l’utilisateur (taille, emplacement, expansion des contrôles de dialogue, et ainsi de suite).

- Vérifiez qu’il n’y a pas d’icône dans la barre de titre.

- Vérifiez qu’il n’y a pas de boutons Minimize et Maximisez dans la barre de titre.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Boutons d’opération de dialogue (VS Client seulement)

- Vérifier que les boutons d’opération sont dans cet ordre: **OK**, **Annuler**, **Appliquer**.

- Vérifiez que les boutons **OK** et **Cancel** sont de la taille standard : 75x23 pixels.

- Vérifiez que les boutons **OK** et **Cancel** sont de taille égale, quelle que soit la longueur des cordes.

- Si l’étiquette sur un bouton d’opération nécessite que le bouton soit plus large que la norme, vérifiez que le bouton **Annuler** correspondant est de taille égale.

- Vérifiez qu’il y a un rembourrage de 6 pixels entre les boutons et les commandes associées.

- Vérifiez que les boutons **OK** et **Annuler** n’ont pas de mnémonique (clés d’accès définies par une lettre soulignée).

- Vérifiez qu’un bouton (généralement **OK**) a la mise au point par défaut.

- Vérifier **qu’Esc** annule le dialogue

- Vérifiez que **Enter** exécute le bouton par défaut si la mise au point n’est pas dans un contrôle qui traite Enter.

- Vérifiez que les boutons **OK** et **Annuler** sont positionnés dans le coin inférieur droit du dialogue. Dans de rares exceptions, il est acceptable qu’ils soient empilés verticalement en haut à droite.

- Vérifiez que la configuration verticale n’est utilisée que si d’autres boutons sont alignés horizontals dans le dialogue.

### <a name="control-standards"></a>Normes de contrôle

#### <a name="general"></a>Général

- Vérifiez que, dans la mesure du possible, il existe de bonnes valeurs par défaut pour accélérer l’interaction avec l’utilisateur et orienter les utilisateurs vers un résultat sûr ou commun.

- Vérifiez que les contrôles standard se comportent de la même manière afin que les utilisateurs sachent ce qui va se passer en fonction de l’expérience antérieure.

#### <a name="label-controls"></a>Contrôles de l’étiquette

- Vérifiez que chaque commande a une étiquette et que chaque étiquette est visuellement jumelée à son contrôle (généralement dans une plage de 4-6 pixels) et est plus proche de son contrôle correspondant que d’autres contrôles.

- Vérifiez que les étiquettes sont positionnées à gauche avec le bord gauche de contrôle s’ils sont positionnés au-dessus et centrés horizontalement, de sorte que la ligne de base de l’étiquette est alignée avec la ligne de base du texte d’entrée si elle est positionnée vers la gauche.

- Vérifiez que si plusieurs commandes d’étiquettes et d’entrées empilées sont positionnées à gauche d’un contrôle, les étiquettes sont à gauche et à une distance égale du bord du dialogue, ne rincer jamais à droite et à une distance égale des commandes. Les paires doivent être réparties uniformément à moins qu’elles n’aient besoin d’espacement supplémentaire pour indiquer le regroupement.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Contrôles d’entrée (boîtes de texte et boîtes combo)

- Vérifiez que lors de l’utilisation de la police de l’environnement par défaut, la hauteur d’affichage pour les boîtes de texte, les boîtes combo et les boutons sont tous 23 pixels.

- Si le texte d’indice est utilisé, vérifiez que la couleur est réglée à l’aide `Environment.ControlEditHintText` du service de couleur.

- Si le champ est un champ requis qui doit être identifié comme tel, vérifiez :

  - que l’arrière-plan est réglé `Environment.ControlEditRequiredBackground` et le premier plan est réglé pour`Environment.ControlEditRequiredHintText`

  - qu’il y a un texte d’indice dans le contrôle qui apparaît comme **«\<> requis »**

#### <a name="button-controls"></a>Contrôles boutons

- Vérifiez que les boutons sont d’une taille minimale de 75x23 pixels, à moins d’accommoder le texte plus long.

- Vérifiez que les boutons ont des marges gauche et droite de 3-5 pixels, ainsi que rembourrage pour le contenu.

- Il est acceptable d’utiliser un petit bouton carré avec seulement une ellipsis **[...]** sur elle au lieu d’un bouton **[Browse...]** (ou une fonctionnalité similaire). S’il est utilisé, vérifiez que le bouton est de 23x23.

- S’il y a plus d’un bouton **[Parcourir...]** dans un dialogue, vérifiez que la version raccourcie (ellipsis-seulement **[...]**) est utilisée pour tous.

- Vérifiez que les boutons d’élipsis **[...]** n’ont pas de mnémonique. Lorsque l’accent est mis sur le contrôle des entrées à côté de lui, un onglet doit se concentrer sur le bouton ellipsis.

- Vérifiez que les boutons, les commandes et les liens de commande qui lancent l’interface utilisateur secondaire qui capture plus d’entrée utilisateur doit se terminer dans une ellipsis **[...]**.

#### <a name="hyperlinks"></a>Liens hypertexte

- Vérifiez qu’un contrôle hyperlien ne clignote jamais en rouge lorsqu’il est actif. Il s’agit d’un indicateur que le service de couleur n’est pas utilisé

- Vérifiez que les couleurs VS utilisées sont les :

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Vérifiez que les hyperliens apparaissent bleus sans souligner à moins d’être intégrés dans un paragraphe.

#### <a name="check-boxes"></a>Cases à cocher

- Si une case à cocher a du texte multi-lignes, vérifiez que la boîte s’aligne avec la première ligne de texte, non centrée verticalement sur toutes les lignes.

- Vérifiez que les cases à cocher indiquent toujours un choix binaire et ne naviguent pas sur l’utilisateur ou n’ouvrent pas de nouvelles fenêtres ou pages.

- Si une case à cocher présente une option liée à un contrôle d’entrée, vérifiez qu’elle est positionnée à gauche et très proche sous ce contrôle pour indiquer sa relation.

- Vérifiez qu’une case à cocher **n’est jamais** utilisée comme moyen d’activer l’ensemble du contenu d’un dialogue ou d’une page.

#### <a name="group-boxes"></a>Boîtes de groupe

- Vérifiez qu’un dialogue ne contient pas une seule boîte de groupe qui contient l’ensemble du contenu du dialogue.

- Vérifiez qu’il y a au moins deux contrôles dans chaque boîte de groupe.

- Il est rare qu’il y ait plus de deux boîtes de groupe sur un dialogue.

- Vérifiez qu’il n’y a pas de boîtes de groupe oischées.

### <a name="icons"></a>Icônes

- Vérifiez que les icônes apparaissent correctement inversées lorsque dans le thème sombre.

- Vérifiez que toutes les icônes sont basées sur des concepts de base.

- Vérifiez que chaque icône est distincte, facile à reconnaître et ne contient pas plus de deux concepts (sans modificateur de statut/langue).

- Vérifiez que l’icône de base apparaît centrée dans l’espace.

- Vérifiez que toutes les icônes apparaissent lisibles en mode contraste élevé.

- Vérifiez que toute couleur utilisée correspond aux normes d’utilisation des couleurs.

- Vérifiez qu’il n’y a pas de halos (frontières) autour des icônes. (Si présent, le halo doit correspondre à la couleur de fond de l’interface utilisateur adjacente).

### <a name="touch-enabled-ui"></a>Interface utilisateur tactile

- Vérifiez que les commandes interactives sont assez grandes pour être facilement tactiles - minimum **23x23 pixels** de taille

- Vérifiez que les commandes les plus fréquemment utilisées sont d’au moins **40x40 pixels** de taille.

- Vérifier que les contrôles interactifs ont au moins **5 pixels d’espacement** entre eux

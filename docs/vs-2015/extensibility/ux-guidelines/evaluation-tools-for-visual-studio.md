---
title: Outils d’évaluation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24ea04e59178248c7a9795a2f928c311ba83db2e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824073"
---
# <a name="evaluation-tools-for-visual-studio"></a>Outils d’évaluation pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Liste de vérification de savoir-faire pour Visual Studio
 Utilisez cette liste pour évaluer la qualité de l’expérience utilisateur pour plus d’informations visuel et d’interaction.

### <a name="overview"></a>Présentation

- Vérifiez que toutes les commandes entraînent des commentaires qui indique aux utilisateurs que leurs commandes ont été effectués.

- Vérifiez que tous les éléments d’interface utilisateur et les contrôles sont visibles dans tous les thèmes et en mode de contraste élevé.

- Vérifiez que sélection active et inactive sont toujours différenciées, à la fois standard et le mode de contraste élevé.

- Vérifiez que le focus est toujours visible et évident.

### <a name="performance"></a>Performances

- Vérifiez que certains indicateurs de type de « occupé » s’affiche si une commande prend plus d’une seconde.

- Vérifiez que si une commande prend plus de 10 secondes, une barre de progression explicite, soit déterminée (recommandé) ou indéterminé, s’affiche.

### <a name="ui-text"></a>Texte de l’interface utilisateur

- Vérifiez que toutes les étiquettes sont phrase ou mots en majuscule et qu’aucun texte n’est entièrement en minuscules.

    ||Corriger|Incorrect|
    |-|-------------|---------------|
    |**Texte de la commande (tout)**|Casse de la phrase :<br /><br /> **Nom du répertoire :**|Nom du répertoire :|
    |**Texte du bouton (client)**|Casse du titre :<br /><br /> **[Définir par défaut]**|SET AS DEFAULT|
    |**Texte du bouton (en ligne)**|Casse de la phrase :<br /><br /> **[Définir comme valeur par défaut]**||

- Vérifiez que toutes les étiquettes, à l’exception des en-têtes de groupe et les boutons, se terminent par un signe deux-points et faites précéder le contrôle avec lequel ils sont associés.

- Vérifiez que les boutons, des commandes et des liens de commande qui lancent l’interface utilisateur pour capturer une entrée d’utilisateur se terminent dans les points de suspension **[...]** .

  Exemples :

  - Un **[Avancé...]**  bouton sur une boîte de dialogue.

  - Les options de commande sous le menu Outils (**Outils > Options**) doit d’obtenir les points de suspension, parce que le lancement de la boîte de dialogue est l’objectif de la commande.

- Vérifiez que l’interface utilisateur ne contient aucun abréviations, à l’exception des termes du contrat standard du secteur. Par exemple, HTML, ni TCP/IP devez explicité, bien que l’insuffisance de mémoire (mémoire insuffisante) et les informations d’identification personnelle (informations d’identification personnelle) doivent.

### <a name="keyboard-access"></a>Accès par le clavier

- Vérifiez qu’il est un moyen d’effectuer chaque tâche à l’aide du clavier. Généralement cela est réalisé via l’accès au clavier pour chaque contrôle, mais pour certaines parties très visuels, tels que de passer en mode code, une solution de contournement est acceptable.

- Vérifiez que la touche Tab via des contrôles dans un ordre logique (de gauche à droite et de haut en bas). Bien que cela soit recommandé pour la plupart des contrôles, pas tous les contrôles nécessitent cette approche. Par exemple, vérifiez que cette case d’option sont des contrôles dans un groupe disposant d’un taquet de tabulation.

- Vérifiez que tous les contrôles ont des étiquettes et que chaque étiquette a un caractère mnémonique (exceptions incluent des contrôles non étiquetés qui peuvent suivre une commande dans l’onglet).

- Vérifiez qu’il n’y a aucun conflit mnémonique.

### <a name="fonts"></a>Polices

- Vérifiez que toutes les polices (face, taille, de couleur) sont utilisés de manière cohérente et conservent la hiérarchie.

- Vérifiez que tous les éléments d’interface utilisateur utilisent le service de police d’environnement. (Consultez [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pour vérifier si le service est utilisé, accédez à **Outils > Options > polices et couleurs**. Dans la liste déroulante des paramètres, choisir la police d’environnement et modifier le type de police à quelque chose de mauvaise différent (par exemple, Harrington ou bande dessinée SAN) et la taille de la valeur est 12 pt. Cliquez ensuite sur OK. Vous devrez peut-être redémarrer l’IDE, mais l’interface utilisateur de la plupart des ne changera pas immédiatement. Les zones qui ne récupèrent pas la modification de la police même lors du redémarrage n’utilisent pas de la police d’environnement.

- Vérifiez que les polices sont dérivé du service (par exemple, texte en gras ou agrandi) conservent leur taille et la mise en forme en relation avec le texte « normal » lorsque la taille de police d’environnement est modifiée.

- Vérifiez qu’il n’y a aucun bogue de découpage en raison de polices agrandis. Polices accrocherait sont probablement le résultat des contrôles de hauteur fixe ou les conteneurs de hauteur fixe.

### <a name="dialogs"></a>Boîtes de dialogue

- Vérifiez que le titre de la boîte de dialogue est identique à la commande qui l’a lancé.

- Vérifiez que tous les contrôles standards sont cohérents avec le système d’exploitation : couleur d’arrière-plan est standard et aucun contrôle ne doit avoir un style basé sur un modèle re spécial qui permet de les rendre différente des contrôles standards.

- Vérifiez que les marges dans le formulaire doivent être de 12 pixels et doivent apparaître uniforme et cohérent.

- Vérifiez que les boîtes de dialogue apparaissent centrés dans l’interpréteur de commandes IDE ou dans la fenêtre qui a généré les.

- Lorsqu’il est utile, boîtes de dialogue doivent être redimensionnables. Pour les boîtes de dialogue redimensionnables, vérifiez que lors de redimensionnement, les contrôles appropriés doivent redimensionner tandis que les autres parties de la boîte de dialogue restent constantes.

- Vérifiez que les boîtes de dialogue redimensionnables conserver n’importe quelle taille ajustée par l’utilisateur (taille, l’emplacement, l’expansion des contrôles de boîte de dialogue et ainsi de suite).

- Vérifiez qu’il n’y a aucune icône dans la barre de titre.

- Vérifiez qu’il n’y a pas de boutons réduire et Agrandir dans la barre de titre.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Boutons d’opération de boîte de dialogue (Visual Studio Client uniquement)

- Vérifiez que les boutons d’opération sont dans cet ordre : **OK**, **Annuler**, **appliquer**.

- Vérifiez que **OK** et **Annuler** boutons sont de taille standard : 75 x 23 pixels.

- Vérifiez que **OK** et **Annuler** boutons sont de taille égale, quel que soit la longueur de chaîne.

- Si l’étiquette sur un bouton d’opération requiert le bouton pour être plus large que standard, vérifiez que le correspondantes **Annuler** bouton est de taille égale.

- Vérifiez qu’il existe une marge intérieure 6-pixel entre les boutons et les contrôles associés.

- Vérifiez que le **OK** et **Annuler** boutons n’ont pas les mnémoniques (touches d’accès définies par une lettre soulignée).

- Vérifiez qu’un bouton (généralement **OK**) a le focus par défaut.

- Vérifiez que **ÉCHAP** annule la boîte de dialogue

- Vérifiez que **entrée** exécute le bouton par défaut si le focus n’est pas dans un contrôle qui traite l’entrée.

- Vérifiez que le **OK** et **Annuler** boutons sont positionnés dans l’angle inférieur droit de la boîte de dialogue. Dans rares exceptions près, il est acceptable pour qu’ils puissent être empilés verticalement en haut à droite.

- Vérifiez que la configuration verticale est utilisée uniquement si les autres boutons sont dans un alignement horizontal dans la boîte de dialogue.

### <a name="control-standards"></a>Normes de contrôle

#### <a name="general"></a>Généralités

- Vérifiez que, lorsque cela est possible, les valeurs par défaut adéquates pour accélérer l’interaction utilisateur et diriger les utilisateurs vers un résultat sans échec ou courantes.

- Vérifiez que les contrôles standard comportent de la même façon afin que les utilisateurs sachent ce qui se produira basée sur l’expérience antérieure.

#### <a name="label-controls"></a>Contrôles Label

- Vérifiez que chaque contrôle possède une étiquette et que chaque étiquette visuellement associé à son contrôle (généralement dans une plage de pixel 4-6) et qu’il est plus proche de son contrôle correspondant qu’à d’autres contrôles.

- Vérifiez que les étiquettes sont positionnées de vidage gauche avec le contrôle si positionnée au-dessus du bord gauche et centré horizontalement, afin que la ligne de base de l’étiquette est alignée avec la ligne de base du texte d’entrée si positionnée à gauche.

- Vérifiez que si plusieurs étiquettes empilées et contrôles d’entrée est positionnés à gauche d’un contrôle, les étiquettes sont alignés à gauche et une distance égale à partir du bord de la boîte de dialogue, vider jamais droite et une distance égale à partir des contrôles. Paires doivent être réparties uniformément, sauf si dont ils ont besoin d’espacement supplémentaire pour indiquer le regroupement.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Contrôles d’entrée (zones de texte et zones de liste déroulante)

- Vérifiez que lorsque vous utilisez la police d’environnement par défaut, la hauteur d’affichage pour les zones de texte, les zones de liste déroulante et les boutons sont tous les 23 pixels.

- Si le texte d’indication est utilisé, vérifiez que la couleur est définie sur `Environment.ControlEditHintText` à l’aide du service de couleur.

- Si le champ est un champ obligatoire qui doit être identifié en tant que tel, vérifiez :

  - que l’arrière-plan est défini sur `Environment.ControlEditRequiredBackground` et premier plan est défini sur `Environment.ControlEditRequiredHintText`

  - texte d’indicateur dans le contrôle qui apparaît sous la forme **»\<requis > »**

#### <a name="button-controls"></a>Contrôles boutons

- Vérifiez que les boutons sont une taille minimale de 75 x 23 pixels, à moins que l’adaptation de texte plus long.

- Vérifiez que les boutons ont quitté et marges de 3 à 5 pixels, ainsi que le remplissage pour le contenu avec le bouton droit.

- Il est acceptable d’utiliser un petit bouton carré des points de suspension uniquement **[...]**  dessus au lieu d’un **[Parcourir...]**  bouton (ou une fonctionnalité similaire). Si utilisé, vérifiez que le bouton est 23 x 23 taille.

- S’il existe plusieurs **[Parcourir...]**  dans une boîte de dialogue, puis vérifiez que la version abrégée (points de suspension uniquement **[...]** ) est utilisé pour tous.

- Vérifiez que points de suspension **[...]**  boutons n’ont pas un caractère mnémonique. Lorsque le focus est sur le contrôle d’entrée en regard de celle-ci, un onglet doit déplacer le focus sur le bouton de sélection.

- Vérifiez que les liens de commande qui lancent l’interface utilisateur secondaire qui capture l’entrée d’utilisateur plus, les commandes et les boutons doivent se terminer dans les points de suspension **[...]** .

#### <a name="hyperlinks"></a>Liens hypertexte

- Vérifiez qu’un contrôle de lien hypertexte jamais clignote en rouge lorsqu’il est actif. Il s’agit d’un indicateur que le service de couleur n’est pas en cours utilisation

- Vérifiez que les couleurs de Visual Studio utilisées sont :

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Vérifiez que des liens hypertexte s’affichent en bleus avec aucun trait de soulignement, sauf si incorporé dans un paragraphe.

#### <a name="check-boxes"></a>Cases à cocher

- Si une case à cocher contient du texte multiligne, vérifiez que la zone s’aligne avec la première ligne de texte, ne pas centré verticalement sur toutes les lignes.

- Vérifiez que cases à cocher toujours indiquer un choix binaire et ne pas diriger l’utilisateur ou ouvrir de nouvelles fenêtres ou des pages.

- Si une case à cocher présente une option liée à un contrôle d’entrée, vérifiez s’il est positionné vidage gauche et très proches sous ce contrôle pour indiquer sa relation.

- Vérifiez qu’une case à cocher est **jamais** utilisé comme un moyen pour activer tout le contenu d’une boîte de dialogue ou une page.

#### <a name="group-boxes"></a>Zones de groupe

- Vérifiez qu’une boîte de dialogue ne contient-elle pas d’une zone de groupe unique qu’il contient qui contient tout le contenu de la boîte de dialogue.

- Vérifiez qu’il n’y a au moins deux contrôles au sein de chaque zone de groupe.

- Rarement doit renfermer plus de deux zones de groupe sur une boîte de dialogue.

- Vérifiez qu’il n’y a aucune boîte groupe imbriqué.

### <a name="icons"></a>Icônes

- Vérifiez que les icônes apparaissent correctement inversés dans le thème sombre.

- Vérifiez que toutes les icônes sont basées sur les concepts fondamentaux.

- Vérifiez que chaque icône est distinct, facile à reconnaître et qu’il ne contient-elle pas plus de deux concepts (sans état modificateur/langage).

- Vérifiez que l’icône de base apparaît centré dans l’espace.

- Vérifiez que toutes les icônes apparaissent lisibles en mode contraste élevé.

- Vérifiez que n’importe quelle couleur utilisé s’aligne avec les normes de l’utilisation de couleur.

- Vérifiez qu’il n’y a aucune halos (bordures) autour des icônes. (Le cas échéant, le halo doit correspondre à la couleur d’arrière-plan de l’interface utilisateur adjacente).

### <a name="touch-enabled-ui"></a>Interface tactile

- Vérifiez que les contrôles interactifs sont suffisamment grandes pour être facilement touchable – minimale **23 x 23 pixels** taille

- Vérifiez que les contrôles les plus fréquemment utilisés sont au moins **40 x 40 pixels** taille.

- Vérifiez que les contrôles interactifs disposent au moins **5 pixels espacement** entre eux

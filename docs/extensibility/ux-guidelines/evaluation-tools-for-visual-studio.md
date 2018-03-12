---
title: "Outils d’évaluation de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7026a14a4880a47f415f5aecd1c15f8a2423d86e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="evaluation-tools-for-visual-studio"></a>Outils d’évaluation de Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Liste de vérification de savoir-faire pour Visual Studio  
 Utilisez cette liste de vérification pour évaluer la qualité de l’expérience utilisateur pour les détails de l’élément visuel et d’interaction.  
  
### <a name="overview"></a>Vue d'ensemble  
  
-   Vérifiez que toutes les commandes entraînent des commentaires qui indique aux utilisateurs que leurs commandes ont été effectués.  
  
-   Vérifiez que tous les éléments d’interface utilisateur et les contrôles sont visibles dans tous les thèmes et en mode de contraste élevé.  
  
-   Vérifiez que la sélection active et inactive toujours se distinguent, en standard et en mode de contraste élevé.  
  
-   Vérifiez que le focus est toujours visible et évident.  
  
### <a name="performance"></a>Performances  
  
-   Vérifiez que l’indicateur de certains types de « occupé » s’affiche si une commande prend plus d’une seconde.  
  
-   Vérifiez que si une commande prend plus de 10 secondes, une barre de progression explicite, soit déterminé (recommandé) ou indéterminé, s’affiche.  
  
### <a name="ui-text"></a>Texte d’interface utilisateur  
  
-   Vérifiez que toutes les étiquettes sont de casse ou de titre et qu’aucun texte n’est entièrement en minuscules.  
  
    ||Corriger|Incorrect|  
    |-|-------------|---------------|  
    |**Texte de la commande (tout)**|Casse de la phrase :<br /><br /> **Nom du répertoire :**|Nom du répertoire :|  
    |**Texte du bouton (client)**|Casse du titre :<br /><br /> **[Définir par défaut]**|VALEUR PAR DÉFAUT EN TANT QUE JEU|  
    |**Texte du bouton (en ligne)**|Casse de la phrase :<br /><br /> **[Défini comme valeur par défaut]**||  
  
-   Vérifiez que toutes les étiquettes, à l’exception des en-têtes de groupe et les boutons, se terminent par un signe deux-points et faites précéder le contrôle avec lequel ils sont associés.  
  
-   Vérifiez que les liens de commandes qui lancent l’interface utilisateur pour capturer l’entrée d’utilisateur, les commandes et les boutons se terminent dans les points de suspension **[...]** .  
  
     Exemples :  
  
    -   Un **[Avancé...]**  bouton sur une boîte de dialogue.  
  
    -   Les options de commande dans le menu Outils (**Outils > Options**) doit d’obtenir les points de suspension, parce que le lancement de la boîte de dialogue est l’objectif de la commande.  
  
-   Vérifiez que l’interface utilisateur ne contienne aucuns abréviation, à l’exception des termes du contrat standard de l’industrie. Par exemple, HTML, ni TCP/IP doivent être formulées, bien que l’insuffisance de mémoire (mémoire insuffisante) et les informations personnelles (informations d’identification personnelle) doivent.  
  
### <a name="keyboard-access"></a>Accès par le clavier  
  
-   Vérifiez qu’il existe un moyen d’effectuer chaque tâche à l’aide du clavier. Généralement cela s’effectue via l’accès clavier pour chaque contrôle, mais pour certaines parties très visuels, une solution de contournement telles que de passer en mode code est acceptable.  
  
-   Vérifiez que vous pouvez onglet via les contrôles dans un ordre logique (de gauche à droite et de haut en bas). Bien que cela soit une meilleure pratique pour la plupart des contrôles, pas tous les contrôles requièrent cette approche. Par exemple, vérifiez que cette case d’option sont des contrôles dans un groupe disposant d’un taquet de tabulation.  
  
-   Vérifiez que tous les contrôles ont des étiquettes et que chaque étiquette a un mnémonique (exceptions incluent certains contrôles non étiqueté qui peuvent suivre une commande dans l’onglet).  
  
-   Vérifiez qu’il n’y a aucun conflit mnémonique.  
  
### <a name="fonts"></a>Polices  
  
-   Vérifiez que toutes les polices (police, taille, couleur) sont utilisées de manière cohérente et conservent la hiérarchie.  
  
-   Vérifiez que tous les éléments d’interface utilisateur utilisent le service de police d’environnement. (Consultez [mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Pour vérifier si le service est utilisé, accédez à **Outils > Options > polices et couleurs**. Dans la liste déroulante de paramètres, choisissez la police d’environnement et modifier le type de police à mots stylistiquement différente (par exemple, Harrington ou dessinée SAN) et définir la taille à 12 pt. Cliquez sur OK. Vous devrez peut-être redémarrer l’IDE, mais la plupart de l’interface utilisateur ne modifie pas immédiatement. Les zones qui ne récupèrent pas la modification de la police lors du redémarrage même n’utilisent pas de la police d’environnement.  
  
-   Vérifiez que les polices sont dérivé du service (par exemple, texte en gras ou agrandie) conservent leur taille et la mise en forme par rapport à texte « normal » lorsque la taille de police d’environnement est modifiée.  
  
-   Vérifiez qu’il n’y a aucun bogue de découpage en raison de polices agrandies. Polices obtient détourés sont probablement le résultat des contrôles de hauteur fixe ou les conteneurs de hauteur fixe.  
  
### <a name="dialogs"></a>Boîtes de dialogue  
  
-   Vérifiez que le titre de la boîte de dialogue est identique à la commande qui a lancé.  
  
-   Vérifiez que tous les contrôles standards sont cohérents avec le système d’exploitation : couleur d’arrière-plan est standard et aucun contrôle ne doit avoir un style de re-basé sur un modèle spécial qui permet de les rendre différent des contrôles standards.  
  
-   Vérifiez que les marges dans le formulaire doivent être de 12 pixels et doivent apparaître uniforme et cohérent.  
  
-   Vérifiez que les boîtes de dialogue apparaissent centrés au sein de l’interface IDE ou dans la fenêtre qui a généré les.  
  
-   Lorsqu’il est utile, boîtes de dialogue doivent être redimensionnables. Pour les boîtes de dialogue redimensionnables, vérifiez que sur le redimensionnement, les contrôles appropriés doivent redimensionner tandis que les autres parties de la boîte de dialogue restent constantes.  
  
-   Vérifiez que les boîtes de dialogue redimensionnables conserver n’importe quelle taille ajustée d’utilisateur (taille, l’emplacement, de contrôles de boîte de dialogue et ainsi de suite).  
  
-   Vérifiez qu’il n’y a pas d’icône dans la barre de titre.  
  
-   Vérifiez qu’il n’y a pas de boutons réduire et Agrandir dans la barre de titre.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Boutons d’opération de boîte de dialogue (Visual Studio Client uniquement)  
  
-   Vérifiez que les boutons d’opération sont dans cet ordre : **OK**, **Annuler**, **appliquer**.  
  
-   Vérifiez que **OK** et **Annuler** boutons sont de taille standard : 75 x 23 pixels.  
  
-   Vérifiez que **OK** et **Annuler** boutons sont de taille égale, quelle que soit la longueur de chaîne.  
  
-   Si l’étiquette sur un bouton d’opération requiert le bouton est plus large que standard, vérifiez que le correspondant **Annuler** bouton est de taille égale.  
  
-   Vérifiez qu’il y a une marge intérieure de 6 pixels entre les boutons et les contrôles associés.  
  
-   Vérifiez que le **OK** et **Annuler** boutons n’ont pas de mnémoniques (touches d’accès définies par une lettre soulignée).  
  
-   Vérifiez qu’un bouton (en général **OK**) a le focus par défaut.  
  
-   Vérifiez que **ÉCHAP** annule la boîte de dialogue  
  
-   Vérifiez que **entrée** exécute le bouton par défaut si le focus ne se trouve pas dans un contrôle qui traite l’entrée.  
  
-   Vérifiez que le **OK** et **Annuler** boutons sont placés dans le coin inférieur droit de la boîte de dialogue. Dans rares exceptions près, il est acceptable pour pouvoir être empilés verticalement dans le coin supérieur droit.  
  
-   Vérifiez que la configuration verticale est utilisée uniquement si les autres boutons sont un alignement horizontal dans la boîte de dialogue.  
  
### <a name="control-standards"></a>Normes de contrôle  
  
#### <a name="general"></a>Général  
  
-   Vérifiez que, lorsque cela est possible, les valeurs par défaut adéquates pour accélérer l’intervention de l’utilisateur et de diriger les utilisateurs vers un résultat sans échec ou courantes.  
  
-   Vérifiez que les contrôles standards comportent de la même manière afin que les utilisateurs savent que se passe-t-il basée sur l’expérience antérieure.  
  
#### <a name="label-controls"></a>Contrôles Label  
  
-   Vérifiez qu’une étiquette à chaque contrôle, et que chaque étiquette visuellement associé à son contrôle (généralement dans une plage de pixel de 4 à 6) et qu’il est plus proche à son contrôle correspondant à d’autres contrôles.  
  
-   Vérifiez que les étiquettes sont positionnées vider gauche avec le contrôle bord gauche si au-dessus et centrée horizontalement, afin que la ligne de base de l’étiquette est aligné avec la ligne de base du texte d’entrée si positionné à gauche.  
  
-   Vérifiez que si plusieurs étiquettes empilées et contrôles d’entrée sont positionnées à gauche d’un contrôle, les étiquettes sont alignés à gauche et une distance égale à partir du bord de la boîte de dialogue vider jamais droite et à égale distance des contrôles. Paires doivent être distribués uniformément, sauf si ils ont besoin d’espace supplémentaire pour indiquer le regroupement.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Contrôles d’entrée (zones de texte et zones de liste déroulante)  
  
-   Vérifiez que lorsque vous utilisez la police d’environnement par défaut, la hauteur d’affichage pour les zones de texte, zones de liste déroulante et les boutons sont 23 pixels de haut.  
  
-   Si le texte d’indication est utilisé, vérifiez que la couleur est définie sur `Environment.ControlEditHintText` à l’aide du service de couleur.  
  
-   Si le champ est un champ obligatoire qui doit être identifié en tant que tel, vérifiez :  
  
    -   que l’arrière-plan est définie sur `Environment.ControlEditRequiredBackground` et premier plan est défini sur`Environment.ControlEditRequiredHintText`  
  
    -   texte d’indication dans le contrôle qui apparaît sous la forme **»\<requise > »**  
  
#### <a name="button-controls"></a>Contrôles boutons  
  
-   Vérifiez que les boutons sont une taille minimale de 75 x 23 pixels, à moins que la prise en charge de texte plus long.  
  
-   Vérifiez que boutons droite et gauche, les marges de 3 à 5 pixels, ainsi que le remplissage pour le contenu.  
  
-   Il est acceptable d’utiliser un petit bouton carré avec des points de suspension uniquement **[...]**  sur celui-ci au lieu d’un **[Parcourir...]**  bouton (ou une fonctionnalité similaire). Si utilisé, vérifiez que le bouton est 23 x 23 taille.  
  
-   S’il existe plusieurs **[Parcourir...]**  dans une boîte de dialogue, puis vérifiez que la version abrégée (points de suspension uniquement **[...]** ) est utilisé pour tous.  
  
-   Vérifiez que points de suspension **[...]**  n’ont pas un mnémonique. Lorsque le focus est sur le contrôle d’entrée correspondante, un onglet doit déplacer le focus sur le bouton points de suspension.  
  
-   Vérifiez que les liens de commandes qui lancent l’interface utilisateur secondaire qui capture l’entrée d’utilisateur plus, les commandes et les boutons doivent se terminer dans les points de suspension **[...]** .  
  
#### <a name="hyperlinks"></a>Liens hypertexte  
  
-   Vérifiez qu’un contrôle de lien hypertexte jamais clignote en rouge lorsqu’il est actif. Il s’agit d’un indicateur que le service de couleur n’est pas en cours utilisation  
  
-   Vérifiez que les couleurs de VS utilisées sont :  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Vérifiez que les liens hypertexte s’affichent en bleus et aucun soulignement à moins qu’incorporé dans un paragraphe.  
  
#### <a name="check-boxes"></a>Cases à cocher  
  
-   Si une case à cocher contient du texte de plusieurs lignes, vérifiez que la zone est alignée avec la première ligne de texte, ne pas centré verticalement sur toutes les lignes.  
  
-   Vérifiez que les cases à cocher toujours indiquent un choix binaire et ne pas l’utilisateur ou ouvrir de nouvelles fenêtres ou les pages.  
  
-   Si une case à cocher présente une option liée à un contrôle d’entrée, vérifiez s’il est positionné aligné à gauche et presque sous ce contrôle pour indiquer sa relation.  
  
-   Vérifiez qu’une case à cocher est **jamais** utilisé comme un moyen pour activer la totalité d’une boîte de dialogue ou une page.  
  
#### <a name="group-boxes"></a>Zones de groupe  
  
-   Vérifiez qu’une boîte de dialogue ne contient pas d’une zone de groupe unique qu’il contient qui contient tout le contenu de la boîte de dialogue.  
  
-   Vérifiez qu’il n’y a au moins deux contrôles dans chaque zone de groupe.  
  
-   Rarement doit renfermer plus de deux zones de groupe sur une boîte de dialogue.  
  
-   Vérifiez qu’il n’y a aucune boîte groupe imbriqué.  
  
### <a name="icons"></a>Icônes  
  
-   Vérifiez que les icônes apparaissent correctement inversés dans le thème sombre.  
  
-   Vérifiez que toutes les icônes sont basées sur les concepts.  
  
-   Vérifiez que chaque icône est distinct, facile à reconnaître et ne contient-elle pas plus de deux concepts (sans état modificateur/langage).  
  
-   Vérifiez que l’icône de base apparaît centré dans l’espace.  
  
-   Vérifiez que toutes les icônes apparaissent lisibles en mode contraste élevé.  
  
-   Vérifiez que n’importe quelle couleur utilisé est alignée avec les normes de l’utilisation de couleur.  
  
-   Vérifiez qu’il n’y a pas ce problème (bordures) autour des icônes. (Le cas échéant, l’éclat doit correspondre à la couleur d’arrière-plan de l’interface utilisateur adjacent).  
  
### <a name="touch-enabled-ui"></a>Interface utilisateur de tactile  
  
-   Vérifiez que les contrôles interactifs sont suffisamment grandes pour être facilement touchable - minimale **23 x 23 pixels** taille  
  
-   Vérifiez que les contrôles les plus fréquemment utilisés sont moins **40 x 40 pixels** taille.  
  
-   Vérifiez que les contrôles interactifs disposent au moins **5 pixels d’espacement** entre eux
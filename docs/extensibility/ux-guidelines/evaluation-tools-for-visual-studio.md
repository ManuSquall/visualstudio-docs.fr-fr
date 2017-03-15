---
title: "Outils d&#39;&#233;valuation de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# Outils d&#39;&#233;valuation de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Liste de vérification de savoir\-faire pour Visual Studio  
 Utilisez cette liste de vérification pour évaluer la qualité de l'expérience utilisateur pour plus d'informations visual et d'interaction.  
  
### Vue d'ensemble  
  
-   Vérifiez que toutes les commandes entraînent des commentaires qui indique aux utilisateurs que leurs commandes ont été effectués.  
  
-   Vérifiez que tous les éléments d'interface utilisateur et les contrôles sont visibles dans tous les thèmes et en mode de contraste élevé.  
  
-   Vérifiez que sélection active et inactive toujours se distinguent, en standard et en mode de contraste élevé.  
  
-   Vérifiez que le focus est toujours visible et évident.  
  
### Performances  
  
-   Vérifiez que certains indicateurs de type de « occupé » s'affiche si une commande prend plus d'une seconde.  
  
-   Vérifiez que si une commande n'accepte plus de 10 secondes pour terminer, une barre de progression explicite, soit déterminé \(recommandé\) ou indéterminé, s'affiche.  
  
### Texte de l'interface utilisateur  
  
-   Vérifiez que toutes les étiquettes sont phrase ou mots en majuscule et qu'aucun texte n'est entièrement en minuscule.  
  
    ||Corriger|Incorrect|  
    |-|--------------|---------------|  
    |**Texte de la commande \(tout\)**|Casse de la phrase :<br /><br /> **Nom du répertoire :**|Nom du répertoire :|  
    |**Texte du bouton \(client\)**|Casse du titre :<br /><br /> **\[Définir par défaut\]**|SET AS DEFAULT|  
    |**Texte du bouton \(en ligne\)**|Casse de la phrase :<br /><br /> **\[Définir comme valeur par défaut\]**||  
  
-   Vérifiez que toutes les étiquettes, à l'exception des en\-têtes de groupe et les boutons, se terminent par un signe deux\-points et faites précéder le contrôle auquel ils sont associés.  
  
-   Vérifiez que les boutons, des commandes et des liens de commande qui lancement l'interface utilisateur pour capturer l'entrée d'utilisateur se terminent dans les points de suspension **\[...\]**.  
  
     Exemples :  
  
    -   Un **\[Avancé...\]** bouton dans une boîte de dialogue.  
  
    -   Les options de commande dans le menu Outils \(**Outils \> Options**\) doit obtenir les points de suspension, parce que le lancement de la boîte de dialogue est l'objectif de la commande.  
  
-   Vérifiez que l'interface utilisateur ne contienne aucuns abréviation, à l'exception des termes du contrat standard de l'industrie. Par exemple, HTML, ni TCP\/IP doivent être formulées, bien que l'insuffisance de mémoire \(mémoire insuffisante\) et les informations personnelles \(informations d'identification personnelle\) doivent.  
  
### Accès par le clavier  
  
-   Vérifiez qu'il existe un moyen pour accomplir chaque tâche à l'aide du clavier. Généralement cela est réalisé via l'accès au clavier pour chaque contrôle, mais pour certaines zones très visuels, tels que passer en mode code, une solution de contournement est acceptable.  
  
-   Vérifiez que vous pouvez onglet via des contrôles dans un ordre logique \(de gauche à droite et de haut en bas\). Il s'agit d'une pratique recommandée pour la plupart des contrôles, pas tous les contrôles de demander cette approche. Par exemple, vérifiez que cette case d'option sont des contrôles dans un groupe disposant d'un taquet de tabulation.  
  
-   Vérifiez que tous les contrôles ont des étiquettes et que chaque contrôle label a un mnémonique \(exceptions incluent certains contrôles non étiquetés qui peuvent suivre une commande dans l'onglet\).  
  
-   Vérifiez qu'il n'y a aucun conflit mnémonique.  
  
### Polices  
  
-   Vérifiez que toutes les polices \(police, taille, couleur\) sont utilisés de manière cohérente et conservent la hiérarchie.  
  
-   Vérifiez que tous les éléments d'interface utilisateur utilisent le service de police d'environnement. \(Voir [Mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)\)  
  
     Pour vérifier si le service est utilisé, accédez à **Outils \> Options \> polices et couleurs**. Dans la liste déroulante de paramètres, choisissez police d'environnement et modifier le type de police à quelque chose de différent mots stylistiquement \(comme Harrington ou bande dessinée SAN\) et définissez la taille de 12 pt. Cliquez ensuite sur OK. Vous devrez peut\-être redémarrer l'IDE, mais la plupart de l'interface utilisateur change immédiatement. Les zones qui ne récupèrent pas la modification de la police même lors du redémarrage n'utilisent pas la police d'environnement.  
  
-   Vérifiez que les polices sont dérivés du service \(par exemple, texte en gras ou agrandi\) conservent leur taille et la mise en forme en relation avec le texte « normal » lorsque la taille de police d'environnement est modifiée.  
  
-   Vérifiez qu'il n'y a pas de bogues découpage en raison de polices élargies. Polices qui obtient ajustées sont probablement le résultat de la hauteur des contrôles ou des conteneurs de hauteur fixe.  
  
### Boîtes de dialogue  
  
-   Vérifiez que le titre de la boîte de dialogue est identique à la commande qui l'a lancé.  
  
-   Vérifiez que tous les contrôles standards sont cohérents avec le système d'exploitation : couleur d'arrière\-plan est standard et aucun contrôle ne doit avoir un style de re\-basé sur un modèle spécial qui permet de les rendre différent des contrôles standards.  
  
-   Vérifiez que les marges dans le formulaire doivent être de 12 pixels et doivent apparaître uniforme et cohérent.  
  
-   Vérifiez que les boîtes de dialogue apparaissent centrés dans l'environnement IDE ou dans la fenêtre qui a généré les.  
  
-   Lorsqu'il est utile, les boîtes de dialogue doivent être redimensionnables. Pour les boîtes de dialogue redimensionnables, vérifiez que sur le redimensionnement, les contrôles appropriés doivent redimensionner tandis que d'autres parties de la boîte de dialogue restent constants.  
  
-   Vérifiez que les boîtes de dialogue redimensionnables conserver n'importe quelle taille ajustées par l'utilisateur \(taille, l'emplacement, l'expansion des contrôles de boîte de dialogue et ainsi de suite\).  
  
-   Vérifiez qu'il n'existe pas d'icône dans la barre de titre.  
  
-   Vérifiez qu'il n'y a pas de boutons Agrandissement et dans la barre de titre.  
  
#### Boutons d'opération de boîte de dialogue \(Visual Studio Client uniquement\)  
  
-   Vérifiez que les boutons sont dans cet ordre : **OK**, **Annuler**, **appliquer**.  
  
-   Vérifiez que **OK** et **Annuler** boutons sont de taille standard : 75 x 23 pixels.  
  
-   Vérifiez que **OK** et **Annuler** boutons sont de taille égale, quelle que soit la longueur de chaîne.  
  
-   Si l'étiquette sur un bouton d'opération requiert le bouton soit plus large que standard, vérifiez que le correspondant **Annuler** bouton est de taille égale.  
  
-   Vérifiez qu'il existe une marge intérieure 6 pixels entre les boutons et les contrôles associés.  
  
-   Vérifiez que le **OK** et **Annuler** n'ont pas mnémoniques \(touches d'accès définis par une lettre soulignée\).  
  
-   Vérifiez qu'un bouton \(en général **OK**\) a le focus par défaut.  
  
-   Vérifiez que **ÉCHAP** annule la boîte de dialogue  
  
-   Vérifiez que **entrée** exécute le bouton par défaut si le focus n'est pas dans un contrôle qui traite l'entrée.  
  
-   Vérifiez que le **OK** et **Annuler** boutons sont positionnés dans le coin inférieur droit de la boîte de dialogue. Dans rares exceptions près, il est acceptable pour qu'ils puissent être empilées verticalement dans le coin supérieur droit.  
  
-   Vérifiez que la configuration verticale est utilisée uniquement si les autres boutons sont un alignement horizontal dans la boîte de dialogue.  
  
### Normes de contrôle  
  
#### Général  
  
-   Vérifiez que, lorsque cela est possible, les valeurs par défaut adéquates pour accélérer l'interaction utilisateur et diriger les utilisateurs vers un résultat sans échec ou courantes.  
  
-   Vérifiez que les contrôles standard comportent de la même manière afin que les utilisateurs savent que se passera\-t\-il basée sur l'expérience antérieure.  
  
#### Contrôles Label  
  
-   Vérifiez que chaque contrôle a une étiquette et que chaque contrôle label visuellement associé à son contrôle \(généralement dans une plage de pixels 4 à 6\) et qu'il est plus proche de son contrôle correspondant à d'autres contrôles.  
  
-   Vérifiez que les étiquettes sont positionnées vider gauche avec le contrôle bord gauche si au\-dessus et centrée horizontalement, afin que la ligne de base de l'étiquette est alignée avec la ligne de base du texte d'entrée si positionnée à gauche.  
  
-   Vérifiez que si plusieurs étiquettes empilées et les contrôles d'entrée sont placés à gauche d'un contrôle, les étiquettes sont alignés à gauche et une distance égale à partir du bord de la boîte de dialogue, vider jamais une distance égale à partir des contrôles et droite. Paires doivent être distribués uniformément sauf dont ils ont besoin d'espace supplémentaire pour indiquer le regroupement.  
  
#### Contrôles d'entrée \(zones de texte et zones de liste déroulante\)  
  
-   Vérifiez que lorsque vous utilisez la police d'environnement par défaut, la hauteur d'affichage de texte, zones de liste déroulante et les boutons sont tous les 23 pixels.  
  
-   Si le texte d'indication est utilisé, vérifiez que la couleur est définie sur `Environment.ControlEditHintText` à l'aide du service de couleur.  
  
-   Si le champ est un champ obligatoire qui doit être identifié en tant que tel, vérifiez :  
  
    -   que l'arrière\-plan est défini sur `Environment.ControlEditRequiredBackground` et premier plan `Environment.ControlEditRequiredHintText`  
  
    -   texte d'indicateur dans le contrôle qui apparaît sous la forme **« \< requis \> »**  
  
#### Contrôles de bouton  
  
-   Vérifiez que les boutons sont une taille minimale de x 23 75 pixels, à moins que la prise en charge de texte plus long.  
  
-   Vérifiez que boutons droite et gauche, les marges de 3 à 5 pixels, ainsi que le remplissage pour le contenu.  
  
-   Il est acceptable d'utiliser un petit bouton carré avec des points de suspension uniquement **\[...\]** dessus au lieu d'un **\[Parcourir...\]** bouton \(ou une fonctionnalité similaire\). Si utilisé, vérifiez que le bouton est 23 x 23 taille.  
  
-   S'il existe plusieurs **\[Parcourir...\]** dans une boîte de dialogue, puis vérifiez que la version abrégée \(points de suspension uniquement **\[...\]**\) est utilisé pour tous.  
  
-   Vérifiez que points de suspension **\[...\]** n'ont pas un mnémonique. Lorsque le focus est sur le contrôle d'entrée correspondante, un onglet doit activer le bouton de sélection.  
  
-   Vérifiez que boutons, des commandes et des liens de commande qui lancement l'interface utilisateur secondaire qui capture l'entrée d'utilisateur plus doivent se terminer par des points de suspension **\[...\]**.  
  
#### Liens hypertexte  
  
-   Vérifiez qu'un contrôle de lien hypertexte jamais clignote en rouge lorsqu'elles sont actives. Il s'agit d'un indicateur que le service de couleur n'est pas en cours utilisation  
  
-   Vérifiez que les couleurs VS sont :  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Vérifiez que les liens hypertexte s'affichent en bleus avec aucun soulignement sauf incorporé dans un paragraphe.  
  
#### Cases à cocher  
  
-   Si une case à cocher contient du texte multiligne, vérifiez que la zone s'aligne avec la première ligne de texte, ne pas centré verticalement sur toutes les lignes.  
  
-   Vérifiez que les cases à cocher toujours indiquent un choix binaire et ne pas l'utilisateur ou ouvrir de nouvelles fenêtres ou les pages.  
  
-   Si une case à cocher présente une option liée à un contrôle d'entrée, vérifiez s'il est positionné aligné à gauche et presque sous ce contrôle pour indiquer sa relation.  
  
-   Vérifiez qu'une case à cocher est **jamais** utilisé comme un moyen pour activer tout le contenu d'une boîte de dialogue ou une page.  
  
#### Zones de groupe  
  
-   Vérifiez qu'une boîte de dialogue ne contient pas qu'il contient une zone de groupe unique qui contient tout le contenu de la boîte de dialogue.  
  
-   Vérifiez qu'il existe au moins deux contrôles dans chaque zone de groupe.  
  
-   Rarement doit renfermer plus de deux zones de groupe dans une boîte de dialogue.  
  
-   Vérifiez qu'il n'y a aucune boîte groupe imbriqué.  
  
### Icônes  
  
-   Vérifiez que les icônes s'affichent correctement inversés dans le thème sombre.  
  
-   Vérifiez que toutes les icônes sont basées sur les concepts fondamentaux.  
  
-   Vérifiez que chaque icône est distinct et facile à reconnaître et ne contient\-elle pas plus de deux concepts \(sans état modificateur\/langage\).  
  
-   Vérifiez que l'icône base centré dans l'espace.  
  
-   Vérifiez que toutes les icônes apparaissent lisibles en mode contraste élevé.  
  
-   Vérifiez que n'importe quelle couleur utilisée s'aligne sur les normes de l'utilisation de couleur.  
  
-   Vérifiez qu'il n'y a aucune halos \(bordures\) autour des icônes. \(Le cas échéant, halo doit correspondre à la couleur d'arrière\-plan de l'interface utilisateur adjacent\).  
  
### Interface tactile  
  
-   Vérifiez que les contrôles interactifs sont suffisamment grandes pour être facilement touchable – minimale **23 x 23 pixels** taille  
  
-   Vérifiez que les contrôles les plus fréquemment utilisés sont moins **40 x 40 pixels** taille.  
  
-   Vérifiez que les contrôles interactifs disposent au moins **5 pixels d'espacement** entre elles
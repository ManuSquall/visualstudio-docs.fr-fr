---
title: "Écrire du code dans l’éditeur de code | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 06cdfb076120ffd7459a16b56c659bb86942cd7f
ms.openlocfilehash: c5e8972cf5efb5596f7649df2c622e802803319f
ms.lasthandoff: 03/31/2017

---
# <a name="write-code-in-the-code-editor"></a>Écrire du code dans l’éditeur de code
L’éditeur Visual Studio fournit de nombreuses fonctionnalités facilitant l’écriture et la gestion de votre code et de votre texte. Vous pouvez développer et réduire différents blocs de code en utilisant le mode Plan. Vous pouvez obtenir plus d’informations sur le code que vous utilisez à l’aide d’IntelliSense, de l’ **Explorateur d’objets**et de la hiérarchie d’appels. Vous pouvez rechercher du code en utilisant des fonctionnalités telles que **Atteindre**, **Atteindre la définition** et **Rechercher toutes les références**. Vous pouvez insérer des blocs de code à l’aide d’extraits de code et vous pouvez générer du code en utilisant des fonctionnalités telles que **Générer à partir de l’utilisation**. Si vous n’avez encore jamais utilisé l’éditeur Visual Studio, consultez [Modification de votre code](https://www.visualstudio.com/features/ide-vs) pour obtenir une vue d’ensemble rapide.  

 Vous pouvez afficher votre code de différentes façons. Pour consulter l’affichage de classes de votre solution, vous pouvez ouvrir la fenêtre **Affichage de classes** ou développer des nœuds dans l’**Explorateur de solutions** sous vos fichiers de classe.

 Vous pouvez rechercher et remplacer du texte pour un ou plusieurs fichiers. Pour plus d’informations, consultez [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md). Vous pouvez utiliser des expressions régulières pour rechercher et remplacer du texte. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Les différents langages de Visual Studio offrent différents ensembles de fonctionnalités et, dans certains cas, les fonctionnalités se comportent différemment dans les différents langages. Un grand nombre de ces différences sont spécifiées dans les descriptions des fonctionnalités, mais pour plus d’informations, vous pouvez consulter les sections relatives aux langages spécifiques de Visual Studio.  

> [!IMPORTANT]
>  L’édition de Visual Studio et les paramètres que vous utilisez peuvent affecter les fonctionnalités de l’environnement IDE. Elles peuvent différer de celles décrites dans cette rubrique.  

## <a name="editor-features"></a>Fonctionnalités de l’éditeur  

|||  
|-|-|  
|Couleurs de syntaxe|Certains éléments de syntaxe des fichiers de code et de balisage apparaissent dans des couleurs différentes pour que vous puissiez les distinguer. Par exemple, les mots clés (tels que `using` en C# et `Imports` en Visual Basic) apparaissent dans une couleur, alors que les types (tels que `Console` et `Uri`) sont d’une autre couleur. D’autres éléments de syntaxe sont également colorés, tels que les commentaires et les littéraux de chaîne. C++ utilise la couleur pour différencier les types, les énumérations et les macros parmi les autres jetons.<br /><br /> Vous pouvez voir la couleur par défaut de chaque type et vous pouvez modifier cette couleur pour tout élément de syntaxe spécifique dans la [boîte de dialogue Polices et couleurs, Environnement, Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que vous pouvez ouvrir à partir du menu **Outils** .|  
|Marques d’erreur et d’avertissement|Quand vous ajoutez du code et générez votre solution, vous pouvez voir s’afficher (a) des soulignements ondulés de différente couleur (les tildes) ou (b) des ampoules dans votre code. Les soulignements ondulés rouges indiquent des erreurs de syntaxe, les soulignements ondulés bleus indiquent des erreurs de compilateur, les soulignements ondulés verts indiquent des avertissements et les soulignements ondulés violets indiquent d’autres types d’erreur. Les [ampoules](../ide/perform-quick-actions-with-light-bulbs.md) suggèrent des solutions aux problèmes rencontrés et facilitent la correction des erreurs.<br /><br /> Vous pouvez voir la couleur par défaut de chaque soulignement ondulé d’erreur et d’avertissement dans la boîte de dialogue **Outils/Options/Environnement/Polices et couleurs** . Recherchez **Erreur de syntaxe**, **Erreur du compilateur**, **Avertissement**et **Autre erreur**.|  
|Accolades correspondantes|Quand le point d’insertion est placé sur une accolade ouvrante dans un fichier de code, l’accolade ouvrante et l’accolade fermante sont mises en surbrillance. Cette fonctionnalité vous permet de visualiser immédiatement les accolades mal placées ou manquantes. Vous pouvez activer ou désactiver la correspondance des accolades à l’aide du paramètre **Mettre les délimiteurs en surbrillance automatiquement** (**Outils/Options/Éditeur de texte**). Vous pouvez modifier la couleur de surbrillance dans le paramètre **Polices et couleurs** (**Outils/Options/Environnement**). Recherchez **Accolades correspondantes (en surbrillance)** ou **Accolades correspondantes (rectangle)**.|  
|Visualiseur de structure|Des lignes en pointillés connectent les accolades correspondantes dans les fichiers de code, permettant de voir plus facilement les paires d’accolades ouvrantes et fermantes. Cela vous permet de trouver plus rapidement du code dans votre code base. Vous pouvez activer ou désactiver ces lignes à l’aide de la case **Afficher les lignes de repère de structure** située dans la section **Affichage** de la page **Outils/Options/Éditeur de texte/Général**.|
|Numéros de ligne|Les numéros de ligne peuvent être affichés dans la marge de gauche de la fenêtre de code. Ils ne sont pas affichés par défaut. Vous pouvez activer cette option dans les paramètres **Éditeur de texte/Tous les langages** (**Outils/Options/Éditeur de texte/Tous les langages**). Vous pouvez afficher les numéros de ligne pour des langages de programmation spécifiques en modifiant les paramètres pour ces langages (**Outils/Options/Éditeur de texte/\<langage>**). Pour imprimer les numéros de ligne, sélectionnez Inclure les numéros de ligne dans la boîte de dialogue **Imprimer** .|  
|Suivi des modifications|La couleur de la marge de gauche vous permet de conserver une trace des modifications effectuées dans un fichier. Les modifications que vous avez effectuées depuis l’ouverture du fichier mais que vous n’avez pas enregistrées sont signalées par une barre jaune dans la marge de gauche (appelée marge de sélection). Une fois que vous avez enregistré les modifications (mais avant la fermeture du fichier), la barre devient verte. Si vous annulez une modification après avoir enregistré le fichier, la barre devient orange. Pour activer et désactiver cette fonctionnalité, modifiez l’option **Suivi des modifications** dans les paramètres **Éditeur de texte** (**Outils/Options/Éditeur de texte**).|  
|Sélection de code et de texte|Vous pouvez sélectionner du texte en mode linéaire standard ou en mode Zone, dans lequel vous sélectionnez une partie rectangulaire du texte au lieu d’un ensemble de lignes. Pour effectuer une sélection en mode Zone, appuyez sur Alt en faisant glisser la souris sur le contenu à sélectionner (ou appuyez sur Alt+Maj+\<touche de direction>). La sélection inclut tous les caractères compris dans le rectangle défini par le premier caractère et le dernier caractère de la sélection. Tout texte tapé ou collé dans la zone sélectionnée est inséré au même endroit sur chaque ligne.|  
|Zoom|Vous pouvez effectuer un zoom avant ou arrière dans n’importe quelle fenêtre de code en maintenant enfoncée la touche Ctrl tout en actionnant la roulette de défilement de la souris (ou en appuyant sur Ctrl+Maj+. pour agrandir l’image et sur Ctrl+Maj+, pour la réduire). Vous pouvez également utiliser la zone zoom dans l’angle inférieur gauche de la fenêtre de code pour définir un pourcentage de zoom spécifique. La fonctionnalité de zoom ne fonctionne pas dans les fenêtres d’outils.|  
|Espace virtuel|Par défaut, les lignes dans les éditeurs Visual Studio se terminent après le dernier caractère, de sorte qu’un appui sur la touche de direction DROITE à la fin d’une ligne place le curseur au début de la ligne suivante. Dans certains autres éditeurs, une ligne ne se termine pas après le dernier caractère et vous pouvez placer le curseur n’importe où sur la ligne. Vous pouvez activer l’espace virtuel dans l’éditeur, dans les paramètres **Outils/Options/Éditeur de texte/Tous les langages** . Notez que vous pouvez activer l’option **Espace virtuel** ou **Retour automatique à la ligne**, mais pas les deux.|  
|Impression|Vous pouvez utiliser les options de la boîte de dialogue **Imprimer** pour inclure les numéros de ligne ou masquer les régions réduites de code quand vous imprimez un fichier. Dans la boîte de dialogue **Mise en page** , vous pouvez également choisir d’imprimer le chemin d’accès complet et le nom du fichier en choisissant **En-tête**.<br /><br /> Vous pouvez définir des options d’impression couleur dans la boîte de dialogue **Outils/Options/Environnement/Polices et couleurs** . Choisissez **Imprimante** dans la liste **Afficher les paramètres de** pour personnaliser l’impression couleur. Vous pouvez spécifier des couleurs différentes pour imprimer un fichier que pour le modifier.|  
|Annulation globale et rétablissement global|Les commandes **Annuler la dernière action globale** et **Rétablir la dernière action globale** du menu **Edition** annulent et rétablissent les actions globales qui affectent plusieurs fichiers. Les actions globales incluent la modification du nom d’une classe ou d’un espace de noms, l’exécution d’une opération de recherche et remplacement dans une solution, la refactorisation d’une base de données ou toute autre action qui modifie plusieurs fichiers. Vous pouvez appliquer les commandes globales d’annulation et de rétablissement aux actions de la session Visual Studio actuelle, même après avoir fermé la solution dans laquelle une action a été appliquée.|  

## <a name="advanced-editing-features"></a>Fonctionnalités d’édition avancées  
 De nombreuses fonctionnalités avancées sont disponibles dans le sous-menu **Edition/Options avancées**. Toutes ces fonctionnalités ne sont pas disponibles pour tous les types de fichiers de code.  

|||  
|-|-|  
|Mettre le document en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans le document.|  
|Mettre la sélection en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans la sélection.|  
|Remplacer les espaces par des tabulations|Remplace les espaces à gauche par des tabulations le cas échéant.|  
|Remplacer les tabulations par des espaces|Remplace les tabulations à gauche par des espaces. Si vous souhaitez convertir tous les espaces de votre fichier en tabulations (ou toutes les tabulations en espaces), vous pouvez utiliser les commandes `Edit.ConvertSpacesToTabs` et `Edit.ConvertTabsToSpaces`. Ces commandes n’apparaissent pas dans les menus de Visual Studio, mais vous pouvez les appeler à partir de la fenêtre Accès rapide ou de la fenêtre Commande.|  
|Mettre en majuscules|Met tous les caractères de la sélection en majuscules ou, en l’absence de sélection, met en majuscule le caractère au point d’insertion.|  
|Mettre en minuscules|Met tous les caractères de la sélection en minuscules ou, en l’absence de sélection, met en minuscule le caractère au point d’insertion.|  
|Déplacer les lignes sélectionnées vers le haut|Déplace la ligne sélectionnée d’une ligne vers le haut. Raccourci : Alt+Flèche haut.|
|Déplacer les lignes sélectionnées vers le bas|Déplace la ligne sélectionnée d’une ligne vers le bas. Raccourci : Alt+Flèche bas.|
|Valider le document|Valide les fichiers de code JScript.|  
|Supprimer les espaces blancs horizontaux|Supprime les tabulations et les espaces à la fin de la ligne active.|  
|Afficher les espaces blancs|Affiche les espaces sous forme de points et les tabulations sous forme de flèches. La fin d’un fichier est indiquée par un glyphe rectangulaire. Si l’option **Outils/Options/Éditeur de texte/Tous les langages/Retour automatique à la ligne/Afficher des glyphes visuels pour le retour automatique à la ligne** est sélectionnée, ce glyphe s’affiche également.|  
|Retour automatique à la ligne|Rend visibles toutes les lignes d’un document dans la fenêtre de code. Vous pouvez activer et désactiver cette option dans les paramètres Tous les langages de l’éditeur de texte (**Outils/Options/Éditeur de texte/Tous les langages**).|  
|Annuler le commentaire de la sélection|Ajoute des caractères de commentaire à la sélection ou à la ligne active.|  
|Commenter la sélection|Supprime les caractères de commentaire de la sélection ou de la ligne active.|  
|Augmenter le retrait de ligne|Ajoute une tabulation (ou les espaces équivalents) aux lignes sélectionnées ou à la ligne active.|  
|Réduire le retrait de ligne|Supprime une tabulation (ou les espaces équivalents) des lignes sélectionnées ou de la ligne active.|  
|Sélectionner la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne la balise.|  
|Sélectionner le contenu de la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne le contenu.|  

## <a name="navigate-and-find-code"></a>Parcourir et rechercher du code  
Vous pouvez vous déplacer dans un document de différentes façons. Outre les opérations standard, vous pouvez utiliser les boutons **Naviguer vers l’arrière** (Ctrl+Moins) et **Naviguer vers l’avant** (Ctrl+Maj+Moins) de la barre d’outils pour déplacer le point d’insertion vers des emplacements précédents ou retourner à des emplacements plus récents dans le document actif. Ces boutons conservent les 20 derniers emplacements du point d’insertion.

![Boutons de navigation Suivant et Précédent](../ide/media/vs2017_nav_buttons.png)

La fonctionnalité Visualiseur de structure de l’éditeur de code montre des *lignes de repère de structure* (lignes en pointillés verticales qui indiquent les accolades correspondantes dans votre code base). Cela permet de voir plus facilement où commencent et où se terminent les blocs logiques.

![Visualiseur de structure](../ide/media/vside_structure_visualizer.png)

Pour désactiver les lignes de repère de structure, accédez à **Outils**, **Options**, **Éditeur de texte**, **Général**, puis décochez la case **Afficher les lignes de repère de structure**.

Vous pouvez également utiliser la barre de défilement améliorée dans une fenêtre de code pour bénéficier d’une vue panoramique de votre code. En mode Plan, vous pouvez afficher des aperçus du code en déplaçant le curseur vers le haut et le bas dans la barre de défilement. Pour plus d’informations, consultez [Guide pratique pour suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

Les commandes suivantes sont des méthodes de navigation spécifiques au code :  

|||  
|-|-|  
|Rechercher toutes les références|(Menu contextuel ou Maj+F12) : recherche toutes les références à l’élément sélectionné dans la solution.|  
|Atteindre|Propose les commandes suivantes : **Atteindre la ligne** (CTRL+G) : accéder au numéro de ligne spécifié dans le document actif. **Atteindre tout** (CTRL+T) : accéder à la ligne, au type, au fichier, au membre ou au symbole spécifié. **Atteindre le fichier** (CTRL+1, CTRL+F) : accéder au fichier spécifié dans la solution. **Atteindre le type** (CTRL+1, CTRL+T) : accéder au type spécifié dans la solution. **Atteindre le membre** (CTRL+1, CTRL+M) : accéder au membre spécifié dans la solution. **Atteindre le symbole** (CTRL+1, CTRL+S) : accéder au symbole spécifié dans la solution. Découvrez plus en détail ces commandes dans la section "Rechercher du code à l’aide des commandes Atteindre", plus loin dans cette rubrique.|  
|Atteindre la définition|(Menu contextuel ou F12) : recherche la définition de l’élément sélectionné.|  
|Accéder à l’implémentation|(Menu contextuel ou CTRL+F12) : recherche l’endroit du code où l’élément sélectionné est implémenté.|
|Aperçu de la définition|(Menu contextuel ou Alt+F12) : recherche la définition de l’élément sélectionné et l’affiche dans une fenêtre de l’éditeur de code. Pour plus d’informations, consultez [Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Méthode suivante, Méthode précédente|(**Edition/Méthode suivante, Méthode précédente**) Dans des fichiers de code Visual Basic, utilisez ces commandes pour déplacer le point d’insertion entre les différentes méthodes.|  
|Mise en surbrillance des références|Quand vous cliquez sur un symbole dans le code source, toutes les instances de ce symbole sont mises en surbrillance dans le document. Les symboles en surbrillance peuvent inclure des déclarations et des références, ainsi que de nombreux autres symboles pouvant être retournés par la fonctionnalité **Rechercher toutes les références** . Ceux-ci incluent les noms de classes, d’objets, de variables, de méthodes et de propriétés. Dans le code Visual Basic, les mots clés de nombreuses structures de contrôle sont également mis en surbrillance. Pour passer au symbole en surbrillance suivant ou précédent, appuyez sur Ctrl+Maj+Bas ou sur Ctrl+Maj+Haut. Vous pouvez modifier la couleur de mise en surbrillance dans **Outils/Options/Environnement/Polices et couleurs/Référence en surbrillance**.|  
|Rechercher des informations relatives au code|Vous pouvez rechercher des informations sur un code spécifique, telles que les modifications et les auteurs de ces modifications, les références, les bogues, les éléments de travail, les révisions du code et l’état de test unitaire quand vous utilisez CodeLens dans l’éditeur de code. CodeLens fonctionne comme un afficheur d’alertes quand vous utilisez Visual Studio Enterprise avec Team Foundation Server. Consultez [Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md).|
|Afficher la hiérarchie d'appels|(Menu contextuel ou CTRL+K, CTRL+T).|  

 Vous pouvez également utiliser la **barre de navigation** (zones de liste déroulante en haut de la fenêtre de code) pour rechercher du code dans un code base. Vous pouvez choisir un type ou un membre pour l’atteindre directement. La barre de navigation s’affiche quand vous modifiez du code dans un code base Visual Basic, C# ou C++.

 ![Barre de navigation dans le code](../ide/media/vside_navigation_bar.png)

 Pour masquer la barre de navigation, changez l’option **Barre de navigation** dans les paramètres Tous les langages de l’éditeur de texte (**Outils**, **Options**, **Éditeur de texte**, **Tous les langages**. Vous pouvez également modifier les paramètres pour des langages spécifiques.) Vous pouvez naviguer dans les zones de liste déroulante comme suit :  

-   Pour déplacer le focus de la fenêtre de code vers la barre de navigation, appuyez sur la combinaison de touches de raccourci Ctrl+F2.  

-   Pour ramener le focus de la barre de navigation dans la fenêtre de code, appuyez sur la touche Échap.  

-   Pour déplacer le focus d’un élément à un autre dans la barre de navigation, appuyez sur la touche Tab.  

-   Pour sélectionner l’élément de la barre de navigation qui a le focus et retourner dans l’environnement IDE, appuyez sur la touche Entrée.  

-   Pour accéder à une classe ou à un type, choisissez son nom dans la liste déroulante gauche.  

-   Pour accéder directement à une procédure dans une classe, choisissez une procédure dans la liste déroulante droite.  

 Dans une classe partielle, les membres définis en dehors du fichier de code actuel peuvent être désactivés (affichés en gris).  

## <a name="find-code-using-go-to-commands"></a>Rechercher du code à l’aide des commandes Atteindre
La commande **Atteindre** de Visual Studio effectue une recherche ciblée dans votre code pour vous aider à trouver rapidement des éléments spécifiés dans les fichiers de code, les chemins de fichiers et les symboles de code. Contrairement à d’autres types de recherche de texte, tels que Rechercher ou Rechercher dans les fichiers, Accéder limite ses recherches aux zones où se trouve le code réel, comme dans des fichiers, des formulaires et des modules de code. Par exemple, si vous recherchez une chaîne dans une application web ASP.NET à l’aide de Rechercher ou de Rechercher dans les fichiers dans l’ensemble de la solution, vous pouvez obtenir des correspondances qui incluent les instances de la chaîne dans les notes du code. Toutefois, l’utilisation d’une commande Atteindre permet à votre recherche de localiser la fonction que vous recherchez en ignorant les instances de la chaîne se trouvant dans des notes de code.

### <a name="find-code-using-go-to"></a>Rechercher du code à l’aide de la commande Atteindre

1. Dans Visual Studio, ouvrez une solution ou un dossier.
1. Dans le menu principal, choisissez **Modifier**, **Atteindre**. Une petite zone de texte s’affiche dans l’angle supérieur de l’éditeur de code.
1. Dans la zone de texte, entrez le nom de l’élément de code que vous souhaitez rechercher.

    ![Fenêtre Naviguer vers](../ide/media/vside_navigatetowindow.png "Fenêtre Naviguer vers")

    À mesure que vous tapez, les résultats s’affichent dans une liste déroulante sous la zone de texte.
1. Pour accéder à un élément, sélectionnez-le dans la liste.


### <a name="filter-your-search"></a>Filtrer votre recherche

Par défaut, l’élément spécifié est recherché dans tous les éléments de solution. Toutefois, vous pouvez limiter votre recherche de code à des types d’éléments spécifiques en faisant précéder les termes de recherche de certains caractères. Le moyen le plus simple d’ouvrir la boîte de dialogue Atteindre consiste à choisir CTRL+T, puis à remplacer le caractère en préfixe par l’un de ceux figurant dans la liste suivante. (Vous pouvez également choisir les touches de raccourci suivantes pour ajouter automatiquement le caractère.)

|Symbole|Description|  
|-|-|
|Aucun|Aucun caractère en préfixe. Le terme spécifié est recherché dans l’ensemble des lignes, fichiers, types, membres et symboles. Raccourci : CTRL+T|
|:|Atteindre le numéro de ligne spécifié. Raccourci : CTRL+G|
|f|Atteindre le nom de fichier spécifié. Raccourci : CTRL+1, CTRL+F|
|t|Atteindre le type spécifié. Raccourci : CTRL+1, CTRL+T|
|m|Atteindre le membre spécifié. Raccourci : CTRL+1, CTRL+M|
|#|Atteindre le symbole spécifié. Raccourci : CTRL+1, CTRL+S|

Par exemple, pour limiter votre recherche aux symboles de code, ouvrez la boîte de dialogue Atteindre en appuyant sur CTRL+T (ou CTRL+,), puis faites précéder la requête Atteindre d’un caractère "#", ou choisissez **Modifier**, **Atteindre**, **Atteindre le symbole** dans le menu. Par exemple, rechercher `# application` affiche uniquement les symboles de code qui contiennent le mot "application".

Vous pouvez aussi changer rapidement le filtre de recherche en choisissant des boutons dans la barre d’outils de la boîte de dialogue Atteindre. Les boutons qui changent les filtres se trouvent à gauche, et les boutons qui changent la portée de la recherche se trouvent à droite.

![](../ide/media/vside_navigation_toolbar.png)

Si vous utilisez la [casse mixte](https://en.wikipedia.org/wiki/Camel_case) dans votre code, vous pouvez trouver plus rapidement des éléments de code en entrant uniquement les lettres majuscules de leur nom. Par exemple, si votre code dispose d’un type appelé `CredentialViewModel`, vous pouvez affiner la recherche en choisissant le filtre Type ("t"), puis en entrant simplement les lettres majuscules du nom (`CVM`) dans la boîte de dialogue Atteindre.

![Fenêtre Naviguer vers - recherche en lettres capitales](../ide/media/vside_capitalsearch.png)

Cette fonctionnalité peut être particulièrement utile si votre code contient des noms longs.

## <a name="finding-references-in-your-codebase"></a>Recherche de références dans votre code base
Pour savoir où des éléments de code particuliers sont référencés dans tout votre code base, vous pouvez utiliser la commande **Rechercher toutes les références**. Pour utiliser **Rechercher toutes les références**, choisissez cette commande dans le menu contextuel (clic droit) de l’élément dont vous voulez rechercher les références, ou choisissez les touches MAJ+F12.

Les résultats s’affichent dans une fenêtre Outil nommée **’*{élément}*’ references**, où *{’élément}* est le nom de l’élément que vous recherchez. Une barre d’outils de cette fenêtre Références vous permet d’effectuer les opérations suivantes :
- Changer la portée de la recherche dans une zone de liste déroulante. Vous pouvez choisir d’effectuer la recherche uniquement dans les documents modifiés dans l’ensemble de la solution.
- Copier l’élément référencé sélectionné en choisissant le bouton **Copier**.
- Pour accéder à l’emplacement suivant ou précédent dans la liste, choisissez les boutons appropriés ou choisissez les touches F8 et MAJ+F8.
- Supprimer tous les filtres sur les résultats retournés en choisissant le bouton **Effacer tous les filtres**.
- Changer la façon dont les éléments retournés sont regroupés en choisissant un paramètre dans la zone de liste déroulante **Grouper par :**.
- Conserver la fenêtre des résultats de la recherche actuelle en choisissant le bouton **Conserver les résultats**.
- Rechercher des chaînes dans les résultats de la recherche en entrant du texte dans la zone de texte **Rechercher toutes les références**.

Vous pouvez également placer le pointeur de la souris sur n’importe quel résultat de la recherche pour afficher un aperçu de l’élément retourné.

![Fenêtre Outil Rechercher toutes les références](../ide/media/vside_findallreferences.png)

Pour conserver les résultats de votre recherche, choisissez le bouton **Conserver les résultats**. Les résultats de la recherche actuelle restent alors dans cette fenêtre, et les résultats des nouvelles recherches s’affichent dans une nouvelle fenêtre Outil.

### <a name="navigate-to-references"></a>Accéder à des références
Dans la boîte de dialogue Rechercher toutes les références, vous pouvez utiliser les méthodes suivantes pour accéder à des références.

- Choisissez F8 pour accéder à la référence suivante, ou MAJ+F8 pour accéder à la référence précédente.
- Choisissez la touche Entrée sur une référence, ou double-cliquez dessus pour y accéder dans le code.
- Dans le menu contextuel d’une référence, choisissez les commandes **Aller à l’emplacement précédent** / **Aller à l’emplacement suivant**.
- Choisissez les touches de direction Haut et Bas (si elles sont activées dans la boîte de dialogue Options). Pour activer cette fonctionnalité, dans le menu, choisissez **Outils**, **Options**, **Environnement**, **Onglets et fenêtres**, **Onglet d’aperçu**, puis cochez les cases **Autoriser l’ouverture des nouveaux fichiers dans l’onglet d’aperçu** et **Afficher les fichiers sélectionnés dans Rechercher les résultats**.

### <a name="change-reference-groupings"></a>Changer les regroupements de références
Par défaut, les références sont regroupées par projet, puis par définition. Toutefois, vous pouvez changer cet ordre de regroupement en changeant le paramètre défini dans la zone de liste déroulante **Grouper par :** de la barre d’outils. Par exemple, vous pouvez le changer en remplaçant le paramètre par défaut **Définition, puis projet** par **Projet, puis définition**, ainsi que par d’autres paramètres.

**Définition** et **Projet** sont les deux regroupements par défaut utilisés, mais vous pouvez en ajouter d’autres en choisissant la commande **Regroupement** dans le menu contextuel de l’élément sélectionné. Il peut être utile d’ajouter plusieurs regroupements si votre solution contient un grand nombre de fichiers et de chemins.

## <a name="customize-the-editor"></a>Personnaliser l’éditeur  
Vous pouvez partager vos paramètres Visual Studio avec un autre développeur, rendre vos paramètres conformes à une norme ou rétablir les paramètres par défaut de Visual Studio à l’aide de la commande **Assistant Importation et exportation de paramètres** du menu **Outils**. Dans l’**Assistant Importation et exportation de paramètres**, vous pouvez changer des paramètres généraux sélectionnés ou des paramètres spécifiques à un langage ou à un projet.

Pour définir de nouvelles touches d’accès rapide ou redéfinir les touches d’accès rapide existantes, accédez à **Outils**, **Options**, **Environnement**, **Claviers**. Pour plus d’informations sur les touches d’accès rapide, consultez [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Pour plus d’informations sur la personnalisation de l’éditeur, consultez [Personnalisation de l’éditeur](../ide/customizing-the-editor.md). Pour plus d’informations sur les options de l’éditeur spécifiques au langage, consultez [Utilisation de l’environnement de développement Visual Studio pour C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) et [Options, Éditeur de texte, JavaScript, Mise en forme](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Voir aussi  
 [IDE Visual Studio](../ide/visual-studio-ide.md)


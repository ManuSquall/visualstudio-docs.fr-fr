---
title: Modèles d’application pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe97972d882fa8806de925bac6a072cd2dde4513
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796879"
---
# <a name="application-patterns-for-visual-studio"></a>Modèles d’application pour Visual Studio
##  <a name="BKMK_WindowInteractions"></a> Interactions de la fenêtre

### <a name="overview"></a>Vue d'ensemble
Les deux types de fenêtre principale utilisées dans Visual Studio sont des éditeurs de document et des fenêtres Outil. Rare mais possible, est grandes boîtes de dialogue non modales. Bien qu’il s’agit tout non modales dans l’interpréteur de commandes, leurs modèles sont fondamentalement différentes. Cette section explique la différence entre les fenêtres de document, les fenêtres Outil et les boîtes de dialogue non modales. Modèles de boîte de dialogue modale couvertes dans [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparaison des modèles d’utilisation de fenêtre
**Fenêtres de document** sont presque toujours affichés dans le document correctement. Ainsi, l’éditeur de document « phase de center » pour réorganiser les fenêtres Outil supplémentaire autour.

Un **fenêtre outil** s’affichent généralement sous forme de fenêtres distincte et plus petite réduit sur le bord de l’IDE. Cela peut être visible, caché ou masqués automatiquement. Cependant, parfois les fenêtres Outil sont présentés dans le document bien, en désactivant le **/ l’ancrage de la fenêtre** propriété dans la fenêtre. Il en résulte davantage de place, mais également la décision de conception commune : lorsque vous tentez d’intégrer à Visual Studio, vous devez décider si votre fonctionnalité doit afficher une fenêtre outil ou une fenêtre de document.

**Boîtes de dialogue non modales** sont déconseillés dans Visual Studio. Boîtes de dialogue plus non modales sont, par définition, les fenêtres Outil flottantes et doivent être implémentés de cette façon. Boîtes de dialogue non modales sont autorisées dans les cas où la taille d’une fenêtre outil normal ancrée sur le côté de l’interpréteur de commandes est trop limitée. Elles sont également autorisées dans les cas où l’utilisateur serait susceptible de déplacer la boîte de dialogue pour une analyse secondaire.

Considérer avec soin sur le type de conteneur vous avez besoin. Utilisation modèle considérations générales pour la conception d’interface utilisateur sont dans le tableau suivant.

||Fenêtre de document|Fenêtre outil|Boîte de dialogue non modale|
|-|---------------------|-----------------|---------------------|
| **Position** | Toujours positionné dans le document bien ne pas ancrer des bords de l’IDE. Il peut être « retiré » afin qu’il flotte séparément à partir de l’interpréteur de commandes principal. | En général sous forme d’onglets autour des bords de l’IDE, mais peut être personnalisé de flottement, masqués automatiquement (non attachés) ou ancré dans le document correctement.|Grande fenêtre flottante distinct à partir de l’IDE. |
| **Valider le modèle** | *Validation différée*<br /><br /> Pour enregistrer les données dans un document, l’utilisateur doit émettre le **fichier &gt; enregistrer**, **enregistrer en tant que**, ou **Enregistrer tout** commande. Une fenêtre de document a le concept des données qu’il contient « modifications » puis validé à un de l’entité commandes. Lors de la fermeture d’une fenêtre de document, tout le contenu est enregistré sur le disque soit perdu. | *Validation immédiate*<br /><br /> Il n’existe aucun enregistrement modèle. Pour les fenêtres d’outil inspecteur qui participent à la modification d’un fichier, le fichier doit être ouvert dans l’éditeur ou concepteur actif, et l’éditeur ou le Concepteur de propriétaire de l’enregistrement. | *Validation retardée ou immédiate*<br /><br /> En règle générale, une boîte de dialogue non modale volumineux nécessite une action de validation des modifications, tout en permettant une opération « Cancel », ce qui annule toutes les modifications apportées dans la session de la boîte de dialogue.  Celle-ci distingue une boîte de dialogue non modale à partir d’une fenêtre outil dans la mesure où les fenêtres Outil ont toujours un modèle de validation immédiate. |
| **Visibilité** | *Open de création (fichier) et de fermeture*<br /><br /> Ouverture d’une fenêtre de document s’effectue via l’ouverture d’un document existant ou à l’aide d’un modèle pour créer un nouveau document. Il existe aucune « Open \<spécifique de l’éditeur > « commande. | *Masquer et afficher*<br /><br /> Windows de l’outil à instance unique peuvent être masquées ou affichées. Contenu et les États dans la fenêtre outil conservent si visible ou masqué. Fenêtres d’outil multi-instance peuvent être fermées mais aussi masqués. Quand une fenêtre outil à instances multiples est fermée, le contenu et l’état dans la fenêtre outil est ignoré. | *Lancée à partir d’une commande*<br /><br /> Boîtes de dialogue sont lancées à partir d’une commande de tâche. |
| **Instances** | *Instances multiples*<br /><br /> Plusieurs éditeurs peuvent être ouverts en même temps et de la modification des fichiers différents, tandis que certains éditeurs autorisent également le même fichier ouvert dans plusieurs éditeurs (à l’aide de la **fenêtre &gt; nouvelle fenêtre** commande).<br /><br /> Un éditeur unique peut modifier un ou plusieurs fichiers en même temps (Concepteur de projet). | *Unique - une ou plusieurs instances*<br /><br /> Contenu change pour refléter le contexte (comme dans l’Explorateur de propriétés) ou focus/contexte vers d’autres fenêtres (liste des tâches, l’Explorateur de solutions).<br /><br /> Les fenêtres Outil à instance unique et multi-instance doivent être associés à la fenêtre de document actif sauf s’il existe une bonne raison de pas à. | *Instance unique* |
| **Exemples** | **Éditeurs de texte**, comme l’éditeur de code<br /><br /> **Les aires de conception**, comme un concepteur de formulaires ou une surface de modélisation<br /><br /> **Contrôler des dispositions similaires pour les boîtes de dialogue**, telles que le Concepteur de manifeste | Le **l’Explorateur de solutions** fournit une solution et projets contenus dans la solution<br /><br /> Le **Explorateur de serveurs** fournit une vue hiérarchique des serveurs et connexions de données que l’utilisateur choisit d’ouvrir dans la fenêtre. Ouverture d’un objet à partir de la hiérarchie de la base de données, comme une requête, ouvre une fenêtre de document et permet à l’utilisateur modifier la requête.<br /><br /> Le **Explorateur de propriétés** affiche les propriétés de l’objet sélectionné dans une fenêtre de document ou une autre fenêtre outil. Les propriétés sont présentées dans une vue hiérarchique de grille ou dans les contrôles de boîtes de dialogue complexes et autoriser l’utilisateur à définir les valeurs de ces propriétés. | |

##  <a name="BKMK_ToolWindows"></a> Fenêtres Outil

### <a name="overview"></a>Vue d'ensemble
Fenêtres Outil prennent en charge de travail de l’utilisateur qui se produit dans les fenêtres de document. Elles peuvent servir pour afficher une hiérarchie qui représente un objet racine fondamental que Visual Studio fournit et peuvent manipuler.

Lorsque vous envisagez une nouvelle fenêtre outil dans l’IDE, les auteurs doivent :

-   Utilisez approprié à la tâche des fenêtres Outil existantes et pas créer d’autres ayant des fonctionnalités similaires. Nouvelles fenêtres Outil doivent être créés uniquement s’ils offrent une très différent « tool » ou une fonctionnalité qui ne peut pas être intégrée dans une fenêtre similaire, ou en activant une fenêtre existante à un concentrateur de croisement dynamique.

-   Utilisez une barre de commandes standard, si nécessaire, en haut de la fenêtre outil.

-   Être cohérente avec les modèles déjà présentes dans les autres fenêtres Outil pour la navigation de clavier et de présentation du contrôle.

-   Être cohérente avec la présentation du contrôle dans les autres fenêtres Outil.

-   Vérifiez les fenêtres Outil de document spécifique visibles automatiquement lorsque cela est possible, afin qu’ils apparaissent uniquement lorsque le document parent est activé.

-   Vérifiez que leur contenu de la fenêtre est navigable par le clavier (prise en charge des touches de direction).

#### <a name="tool-window-states"></a>États de la fenêtre outil
Fenêtres Outil Visual Studio ont des états différents, certains d'entre eux sont activés par utilisateur (par exemple, la fonctionnalité de masquage automatique). Autres États, comme visibles automatiquement, autoriser les fenêtres Outil apparaisse dans le contexte approprié et masquer lorsque ne pas nécessaires. Il existe cinq États de la fenêtre outil au total.

-   **Ancré/épinglé** fenêtres Outil peuvent être attachés à l’un des quatre côtés de la zone de document. L’icône de punaise apparaît dans la barre de titre de fenêtre outil. La fenêtre outil peut être ancrée horizontalement ou verticalement le long du bord de l’interpréteur de commandes et d’autres fenêtres Outil et peut également être liée par onglets.

-   **Masqués automatiquement** fenêtres Outil sont libérés. La fenêtre peut glisser hors de vue, en laissant un onglet (avec le nom de la fenêtre outil et son icône) sur le bord de la zone de document. La fenêtre outil sont extraites quand un utilisateur pointe sur l’onglet.

-   **Visibles automatiquement** fenêtres Outil apparaissent automatiquement lorsqu’une autre partie de l’interface utilisateur, comme un éditeur, est lancée ou obtention du focus.

-   **Flottante** fenêtres Outil placez le curseur en dehors de l’IDE. Cela est utile pour les configurations de plusieurs écrans.

-   **Document à onglets** fenêtres Outil peuvent être ancrées dans le document correctement. Cela est utile pour les grandes fenêtres, telles que l’Explorateur d’objets, nécessitant davantage de place que ne le permet d’ancrage sur les bords du cadre.

![Outil d’états de la fenêtre dans Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />États de la fenêtre Outil dans Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instance unique et multi-instance
Fenêtres Outil sont à instance unique ou multi-instance. Certaines fenêtres Outil à instance unique peuvent être associées à la fenêtre de document actif, tandis que les fenêtres d’outil multi-instance ne peut-être pas. Les fenêtres Outil multi-instances répondent à la **fenêtre &gt; nouvelle fenêtre** commande en créant une nouvelle instance de la fenêtre. L’image suivante illustre une fenêtre outil l’activation de la commande nouvelle fenêtre lorsqu’une instance de la fenêtre est active :

![Fenêtre outil activant des commandes « Nouvelle fenêtre » lorsqu’une instance de la fenêtre est active](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Fenêtre outil activant des commandes « Nouvelle fenêtre » lorsqu’une instance de la fenêtre est active

Windows de l’outil à instance unique peuvent être masquées ou affichées, alors que les fenêtres d’outil à instances multiples peuvent être fermés ainsi que masqués. Toutes les fenêtres Outil peuvent être ancrées, liée par onglets, flottante ou définie comme une fenêtre d’enfant d’Interface multidocument (MDI) (semblable à une fenêtre de document). Toutes les fenêtres Outil doivent répondre aux commandes de gestion de fenêtre approprié dans le menu Fenêtre :

![Commandes de gestion de fenêtre dans le menu Fenêtre Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Commandes de gestion de fenêtre dans le menu Fenêtre Visual Studio

#### <a name="document-specific-tool-windows"></a>Fenêtres de document spécifique
Certaines fenêtres Outil sont conçus pour changer en fonction d’un type de document donné. Ces fenêtres continuellement mise à jour pour refléter les fonctionnalités sont applicables à la fenêtre de document actif dans l’IDE.

La boîte à outils et la structure du Document sont des exemples de fenêtres Outil dont le contenu sont modifiés pour refléter l’éditeur sélectionné. Ces fenêtres montrent un filigrane quand un éditeur a le focus qui n’offre pas de contexte à la fenêtre.

#### <a name="navigable-list-tool-windows"></a>Fenêtres d’outil liste navigable
Certaines fenêtres Outil affichent une liste d’éléments navigables, avec que l’utilisateur peut interagir. Dans ce type de fenêtre, il doit toujours y avoir des commentaires pour l’élément actuel dans la liste, même si la fenêtre est inactive. La liste doit répondre à la **GoToNextLocation** et **GoToPrevLocation** commandes en modifiant également l’élément actuellement sélectionné dans la fenêtre

L’Explorateur de solutions et de la fenêtre Résultats de la recherche sont des exemples de fenêtres d’outil liste navigable.

### <a name="tool-window-types"></a>Types de fenêtres Outil

#### <a name="common-tool-windows-and-their-functions"></a>Fenêtres d’outils courants et leurs fonctions

**Fenêtres Outil hiérarchique**

| Fenêtre outil | Fonction |
| --- | --- |
| Explorateur de solutions | Une arborescence hiérarchique qui affiche la liste des documents contenus dans des projets, les fichiers divers et les éléments de solution. L’affichage des éléments dans des projets est défini par le package qui possède le type de projet (par exemple, en fonction de référence basée sur le répertoire, types ou en mode mixte). |
| Affichage de classes | Une arborescence hiérarchique des classes et des différents éléments dans la plage de travail de documents, indépendamment des fichiers eux-mêmes. |
| Explorateur de serveurs | Une arborescence hiérarchique qui affiche toutes les connexions de serveurs et les données de la solution. |
| Structure du document | La structure hiérarchique du document actif. |

**Fenêtres Outil de grille**

| Fenêtre outil | Fonction |
| --- | --- |
| Properties | Une grille qui affiche une liste de propriétés de l’objet sélectionné, ainsi que les sélecteurs de valeur pour modifier ces propriétés. |
| Liste des tâches | Une grille qui permet à l’utilisateur à créer, modifier ou supprimer des tâches et des commentaires. |

**Fenêtres Outil de contenu**

| Fenêtre outil | Fonction |
| --- | --- |
| Aide | Une fenêtre qui permet aux utilisateurs l’accès à différentes méthodes d’obtention d’aide, à partir de « Comment faire ? » vidéos sur les forums MSDN. |
| Aide dynamique | Une fenêtre outil qui affiche des liens vers des rubriques applicables à la sélection actuelle d’aide. |
| Explorateur d'objets | Un jeu de cadres de deux colonnes avec une liste des composants hiérarchique d’objets dans le volet gauche de l’objet propriétés et méthodes dans la colonne de droite. |

**Fenêtres Outil de boîte de dialogue**

| Fenêtre outil | Fonction |
| --- | --- |
| Find | Une boîte de dialogue qui permet à l’utilisateur à rechercher ou rechercher et remplacer dans les fichiers divers dans la solution. |
| Recherche avancée | Une boîte de dialogue qui permet à l’utilisateur à rechercher ou rechercher et remplacer dans les fichiers divers dans la solution. |

**Autres fenêtres Outil**

::: moniker range="vs-2017"

| Fenêtre outil | Fonction |
| --- | --- |
| Boîte à outils | La fenêtre outil est utilisée pour stocker les éléments qui sont supprimés sur les surfaces de conception, en fournissant une source de glissement cohérente pour tous les concepteurs. |
| Page de démarrage | Portail de l’utilisateur pour Visual Studio, avec un accès aux flux de l’actualité des développeurs, l’aide de Visual Studio et projets récents. Les utilisateurs peuvent également créer des pages de démarrage personnalisées en copiant le fichier StartPage.xaml à partir de la « Common7\IDE\StartPages\" directory et puis soit en modifiant le XAML des documents de répertoire des fichiers programme Visual Studio dans le dossier StartPages dans Visual Studio à la main ou ouvrez-le dans Visual Studio ou un autre éditeur de code. |

::: moniker-end

::: moniker range=">=vs-2019"

| Fenêtre outil | Fonction |
| --- | --- |
| Boîte à outils | La fenêtre outil est utilisée pour stocker les éléments qui sont supprimés sur les surfaces de conception, en fournissant une source de glissement cohérente pour tous les concepteurs. |

::: moniker-end

**Fenêtres du débogueur**

| Fenêtre outil | Fonction |
| --- | --- |
| Automatique ||
| Immédiat ||
| Sortie | La fenêtre de sortie peut être utilisée chaque fois que vous avez des événements textuelles ou état pour déclarer. |
| Mémoire ||
| Points d'arrêt ||
| Exécution en cours ||
| Documents ||
| Pile des appels ||
| Variables locales ||
| Espions ||
| Code machine ||
| 3DNow! ||
| Threads ||

##  <a name="BKMK_DocumentEditorConventions"></a> Conventions de l’éditeur de document

### <a name="document-interactions"></a>Interactions de document
« Bien document » est le plus grand espace au sein de l’IDE et où l’utilisateur générale s’est concentré leur attention afin de terminer leurs tâches, assistés par des fenêtres d’outils supplémentaires. Les éditeurs de document représentent les unités de base de travail que l’utilisateur s’ouvre et enregistre au sein de Visual Studio. Elles conservent une forte de sélection liée à l’Explorateur de solutions ou d’autres fenêtres de la hiérarchie active. L’utilisateur doit être en mesure de pointer vers un de ces fenêtres de hiérarchie et de savoir où se trouve le document et sa relation à la solution, le projet ou un autre objet racine fourni par un package Visual Studio.

Modification de documents nécessite une expérience utilisateur cohérente. Pour autoriser l’utilisateur de se concentrer sur la tâche en cours à la place de gestion des fenêtres et la recherche de commandes, sélectionnez une stratégie d’affichage de document qui répond le mieux aux tâches d’utilisateur pour la modification de ce type de document.

#### <a name="common-interactions-for-the-document-well"></a>Interactions communes pour le document bien

-   Mettre à jour un modèle d’interaction cohérente en le commun **nouveau fichier** et **ouvrir un fichier** expériences.

-   Mettre à jour des fonctionnalités connexes dans les menus et fenêtres associées lors de la fenêtre de document s’ouvre.

-   Commandes de menu sont correctement intégrées dans les menus courants tels que **modifier**, **Format**, et **vue** menus. Si une quantité substantielle de commandes spécialisées est disponible, un nouveau menu peut être créé. Ce nouveau menu doit être visible uniquement lorsque le document a le focus.

-   Une barre d’outils incorporée peut être placé en haut de l’éditeur. Cela est préférable d’avoir une barre d’outils distinct qui s’affiche en dehors de l’éditeur.

-   Toujours conserver une sélection dans l’Explorateur de solutions ou d’un actif similaire fenêtre hiérarchie.

-   Double-cliquez sur un document dans l’Explorateur de solutions doit effectuer la même action que **Open**.

-   Si plus d’un éditeur peut être utilisé sur un type de document, l’utilisateur doit être en mesure de remplacer ou de réinitialiser l’action par défaut sur un type de document donné à l’aide de la **ouvrir avec** boîte de dialogue en cliquant sur le fichier et en sélectionnant **ouvert Avec** dans le menu contextuel.

-   Ne créez pas également un Assistant dans un document.

### <a name="user-expectations-for-specific-document-types"></a>Attentes de l’utilisateur pour les types de document spécifique
Il existe plusieurs types de base différents éditeurs de document et chacun possède un ensemble d’interactions sont cohérents avec d’autres utilisateurs du même type.

-   **Éditeur de texte :** éditeur de code, les fichiers journaux

-   **Aire de conception :** Formulaires de Windows concepteur, WPF forms

-   **Éditeur de style de la boîte de dialogue :** Concepteur de manifeste, propriétés du projet

-   **Générateur de modèles :** Concepteur de workflow, codemap, diagramme d’architecture, progression

Il existe également plusieurs types non éditeur qui utilisent le document correctement. Pendant qu’ils ne modifiez pas les documents eux-mêmes, elles doivent suivre des interactions standard pour les fenêtres de document.

-   **Rapports :** Rapport d’IntelliTrace, rapport de Hyper-V, le rapport de profileur

-   **Tableau de bord :** Concentrateur de diagnostic

#### <a name="text-based-editors"></a>Éditeurs de texte

-   Le document participe au modèle onglet Aperçu pour afficher un aperçu du document sans l’ouvrir.

-   La structure du document peut être représentée dans une fenêtre d’outil d’accompagnement, comme une structure du document.

-   IntelliSense (le cas échéant) se comporte de manière cohérente avec les autres éditeurs de code.

-   Les fenêtres contextuelles ou l’interface utilisateur d’assistance suivre les styles et modèles similaires pour l’interface utilisateur similaire existante, telles que CodeLens.

-   Messages concernant l’état du document seront affiche dans un contrôle de barre d’informations en haut du document ou dans la barre d’état.

-   L’utilisateur doit être en mesure de personnaliser l’apparence des polices et couleurs à l’aide un **Outils > Options** page, la page polices et couleurs partagée ou spécifiques à un à l’éditeur.

#### <a name="design-surfaces"></a>Surfaces de dessin

-   Un concepteur vide doit avoir un filigrane sur l’aire d’indiquant comment commencer.

-   Mécanismes de basculement entre les vues suit les modèles existants comme double-clic pour ouvrir un éditeur de code ou des onglets dans la fenêtre de document permettant l’interaction avec les deux volets.

-   Ajout d’éléments à l’aire de conception doit être effectuée par le biais de la boîte à outils, sauf si une fenêtre outil très spécifique est requise.

-   Éléments sur l’aire suivent un modèle de sélection cohérente.

-   Barres d’outils incorporées contiennent des commandes d’uniquement, pas courants des commandes spécifiques au document comme **enregistrer**.

#### <a name="dialog-style-editors"></a>Éditeurs de style de la boîte de dialogue

-   Disposition des contrôles doit suivre les conventions de mise en page des boîtes de dialogue.

-   Onglets de l’éditeur ne doivent pas correspondre à l’apparence des onglets de document, elles doivent correspondre à un des deux styles onglet intérieurs autorisées.

-   Les utilisateurs doivent être en mesure d’interagir avec les contrôles à l’aide du clavier uniquement ; soit par activation de l’éditeur et la tabulation via des contrôles ou à l’aide de mnémoniques standards.

-   Le concepteur doit utiliser courantes enregistrer le modèle. Aucun enregistrement global ou un bouton de validation ne doit être placé sur la surface, bien que les autres boutons peuvent être appropriées.

#### <a name="model-designers"></a>Concepteurs de modèles

-   Un concepteur vide doit avoir un filigrane sur l’aire d’indiquant comment commencer.

-   Ajout d’éléments à l’aire de conception doit être effectuée par le biais de la boîte à outils.

-   Éléments sur l’aire suivent un modèle de sélection cohérente.

-   Barres d’outils incorporées contiennent des commandes d’uniquement, pas courants des commandes spécifiques au document comme **enregistrer**.

-   Une légende peut apparaître sur la surface, indicative ou filigrane.

-   L’utilisateur doit être en mesure de personnaliser l’apparence des polices/couleurs à l’aide un **Outils > Options** page, la page polices et couleurs partagée ou spécifiques à un à l’éditeur.

#### <a name="reports"></a>Rapports

-   Les rapports sont généralement uniquement des informations et ne font pas partie du modèle d’enregistrement. Toutefois, elles peuvent inclure des interactions telles que des liens vers d’autres informations pertinentes ou les sections qui développés ou réduits.

-   La plupart des commandes sur la surface doivent être des liens hypertexte, pas de boutons.

-   Mise en page doit inclure un en-tête et suivez les instructions de mise en page de rapport standard.

#### <a name="dashboards"></a>Tableaux de bord

-   Tableaux de bord n’ont un modèle d’interaction eux-mêmes, mais comme un moyen d’offrent un large éventail d’autres outils.

-   Elles n’interviennent pas dans le modèle de sauvegarde.

-   Les utilisateurs doivent pouvoir interagir avec les contrôles à l’aide du clavier uniquement, en activant l’éditeur et de tabulation via des contrôles ou à l’aide de mnémoniques standards.

##  <a name="BKMK_Dialogs"></a> Boîtes de dialogue

### <a name="introduction"></a>Introduction
Boîtes de dialogue dans Visual Studio doivent généralement prendre en charge d’une unité discrète de travail de l’utilisateur et ensuite être fermées.

Si vous avez déterminé que vous avez besoin d’une boîte de dialogue, vous avez trois possibilités, par ordre de préférence :

1.  Intégrer des fonctionnalités dans une des boîtes de dialogue partagés dans Visual Studio.

2.  Créer votre propre boîte de dialogue à l’aide d’un modèle trouvé dans une boîte de dialogue similaire existant.

3.  Créer une nouvelle boîte de dialogue, l’interaction suivante et instructions de disposition.

Cette section décrit comment choisir le modèle de boîte de dialogue correct au sein de flux de travail de Visual Studio et les conventions courantes pour la conception de la boîte de dialogue.

### <a name="themes"></a>Thèmes
Boîtes de dialogue dans Visual Studio suivent l’une des deux styles de base :

#### <a name="standard-unthemed"></a>Standard (unthemed)
La majorité des boîtes de dialogue sont les boîtes de dialogue utilitaire standard et doit être unthemed. Ne pas les contrôles communs remodéliser, ou essayez de créer des boutons « modernes » stylisés ou contrôles. Contrôles et l’apparence de chrome suivez [directives d’interaction de bureau de Windows standards pour les boîtes de dialogue](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>À thème
Boîtes de dialogue spécialité « signature » peuvent être à thème. Boîtes de dialogue à thème ont une apparence distincte, ce qui a également des modèles d’interaction spéciale associées au style. Thème de votre boîte de dialogue uniquement si elle répond à ces exigences :

-   La boîte de dialogue est une expérience commune qui sera vu et utilisée souvent ou par de nombreux utilisateurs (par exemple, le **nouveau projet** boîte de dialogue.

-   La boîte de dialogue contient les éléments de marque de produit visible (par exemple, le **comptable** boîte de dialogue).

-   La boîte de dialogue s’affiche en tant que partie intégrante d’un plus grand flux qui inclut d’autres boîtes de dialogue à thème (par exemple, le **ajouter un Service connecté** boîte de dialogue).

-   La boîte de dialogue est une partie importante d’une expérience qui joue un rôle stratégique dans la promotion ou ce qui différencie une version du produit.

Lorsque vous créez une boîte de dialogue à thème, utiliser les couleurs d’environnement appropriées et suivez la disposition correcte et les modèles d’interaction. (Consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Conception de la boîte de dialogue
Boîtes de dialogue bien conçues tenir compte les éléments suivants :

-   La tâche de l’utilisateur qui est pris en charge

-   La boîte de dialogue style de texte, la langue et la terminologie

-   Choix de contrôle et les conventions de l’interface utilisateur

-   Alignement de spécification et le contrôle de disposition visuelle

-   Accès par le clavier

#### <a name="content-organization"></a>Organisation du contenu
Prenez en compte les différences entre ces types de base de boîtes de dialogue :

-   [Boîtes de dialogue simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) présenter des contrôles dans une seule fenêtre modale. La présentation peut inclure des variantes de modèles de contrôle complexe, y compris un sélecteur de champ ou une barre d’icônes.

-   [Couches de boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) sont utilisés pour faire le meilleur parti de l’écran lorsqu’un seul élément de l’interface utilisateur comporte plusieurs groupes de contrôles. Les regroupements de la boîte de dialogue sont « superposées » via les contrôles d’onglet, les contrôles de liste de navigation ou des boutons afin que l’utilisateur peut choisir lequel le regroupement pour voir à un moment donné.

-   [Assistants](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sont utiles pour la redirection de l’utilisateur via une séquence d’étapes vers la fin d’une tâche logique. Une série de choix sont proposés dans les panneaux séquentiel, parfois présentation différents flux de travail (« branches ») dépend d’un choix dans le panneau précédent.

####  <a name="BKMK_SimpleDialogs"></a> Boîtes de dialogue simples
Une boîte de dialogue simple est une présentation des contrôles dans une seule fenêtre modale. Cette présentation peut inclure des variantes de modèles de contrôle complexe, tel qu’un sélecteur de champ. Pour les boîtes de dialogue simples, suivez la disposition générale standard, ainsi que toute disposition spécifique requise pour les regroupements de contrôle complexe.

![> créer une clé de nom fort est un exemple d’une boîte de dialogue simple dans Visual Studio. ](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Créer une clé de nom fort est un exemple d’une boîte de dialogue simple dans Visual Studio.

####  <a name="BKMK_LayeredDialogs"></a> Boîtes de dialogue en couches
Boîtes de dialogue en couche incluent les onglets, les tableaux de bord et les arbres incorporés. Ils sont utilisés pour optimiser l’immobilier lorsqu’il y a plusieurs groupes de contrôles proposés dans un seul élément de l’interface utilisateur. Les regroupements sont superposées afin que l’utilisateur peut choisir lequel le regroupement pour afficher à tout moment.

Dans le cas le plus simple, le mécanisme de commutation entre les regroupements est un contrôle onglet. Il existe plusieurs alternatives disponibles. Consultez la définition de la priorité et superposition pour savoir comment choisir le style plus approprié.

Le **outils &gt; Options** boîte de dialogue est un exemple d’une boîte de dialogue superposée à l’aide d’une arborescence incorporée :

![Outils > Options est un exemple d’une boîte de dialogue superposée dans Visual Studio. ](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Outils > Options est un exemple d’une boîte de dialogue superposée dans Visual Studio.

####  <a name="BKMK_Wizards"></a> Assistants
Assistants sont utiles pour la redirection de l’utilisateur via une séquence logique d’étapes dans la réalisation d’une tâche. Une série de choix sont proposés dans les panneaux séquentiel, et l’utilisateur doit continuer à chaque étape avant de passer à la suivante. Une fois que les valeurs par défaut suffisantes sont disponibles, le **Terminer** bouton est activé.

 Assistants modales utilisées pour les tâches qui :

-   Contient la création de branches, où les différents chemins d’accès sont proposées en fonction des choix de l’utilisateur

-   Contient des dépendances entre les étapes, où les étapes suivantes dépendent des entrées utilisateur à partir de l’ou les étapes précédente

-   Sont suffisamment complexe pour que l’interface utilisateur doit être utilisé pour expliquer les choix proposés et les résultats possibles dans chaque étape

-   Sont transactionnelles, nécessitant un ensemble d’étapes à effectuer dans son intégralité avant que toutes les modifications soient validées

### <a name="common-conventions"></a>Conventions communes
Pour obtenir la conception optimale et des fonctionnalités avec vos boîtes de dialogue, suivez ces conventions sur la taille de la boîte de dialogue, position, normes, configuration de contrôle et l’alignement, l’interface utilisateur texte, barres de titre, les boutons de contrôle et clés d’accès.

Pour obtenir des instructions spécifiques à la disposition, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Taille
Boîtes de dialogue doivent tenir dans une résolution d’écran de 1024 x 768 minimale, et la taille de la boîte de dialogue initiale ne doit pas dépasser 900 x 700 pixels. Boîtes de dialogue peuvent être redimensionnables, mais il n’est pas obligatoire.

Il existe deux recommandations pour les boîtes de dialogue redimensionnables :

1.  Qu’une taille minimale est définie pour la boîte de dialogue qui vous permettra d’optimiser pour le contrôle définir sans découpage et ajuster pour répondre à la croissance de localisation raisonnable.

2.  Que la taille de la mise à l’échelle utilisateur persiste à partir d’une session à l’autre. Par exemple, si l’utilisateur redimensionne une boîte de dialogue à 150 %, un lancement suivant de la boîte de dialogue affichera à 150 %.

#### <a name="position"></a>Position
Boîtes de dialogue doivent apparaître centrés dans l’IDE lors du premier lancement. La dernière position de boîtes de dialogue non redimensionnable n’a pas besoin être rendue persistante, et ils s’affichent centrés sur les lancements suivants.

Pour les boîtes de dialogue redimensionnables, la taille doit être persistante sur les lancements suivants. Pour les boîtes de dialogue modales redimensionnables, la position n’a pas besoin être rendue persistante. Leur affichage centré dans l’IDE empêche la possibilité de la boîte de dialogue apparaissant dans une position imprévisible ou inutilisable lors de la configuration de l’affichage de l’utilisateur a changé.

Pour les boîtes de dialogue non modales qui peuvent être repositionnés, position de l’utilisateur doit être conservée sur les lancements suivants, car la boîte de dialogue peut être utilisée fréquemment en tant que partie intégrante d’un flux de travail plus volumineux.

Lorsque les boîtes de dialogue doivent générer d’autres boîtes de dialogue, la boîte de dialogue au premier plan doit mettre en cascade vers la droite et vers le bas à partir du parent de sorte qu’il évidente à l’utilisateur que vous leur ont navigué vers un nouvel emplacement.

#### <a name="modality"></a>Modalité
Modal en cours signifie que les utilisateurs sont requis pour terminer ou annuler la boîte de dialogue avant de continuer. Dans la mesure où les boîtes de dialogue modales empêchent l’utilisateur d’interagir avec d’autres parties de l’environnement, les flux de tâches de votre fonction doivent les utiliser avec parcimonie que possible. Lorsqu’une opération modale est nécessaire, Visual Studio a un nombre de boîtes de dialogue partagées dans que vous pouvez intégrer des fonctionnalités. Si vous devez créer une nouvelle boîte de dialogue, suivez le modèle d’interaction d’un dialogue existant ayant des fonctionnalités similaires.

Lorsque les utilisateurs doivent effectuer les deux activités à la fois, comme **trouver** et **remplacer** lors de l’écriture de nouveau code, la boîte de dialogue doit être non modale afin que l’utilisateur peut basculer facilement entre eux. Visual Studio utilise généralement des fenêtres Outil pour ce type de prise en charge de l’éditeur de tâche liée.

#### <a name="control-configuration"></a>Configuration de contrôle
Être compatible avec les configurations de contrôle existant qui accomplissent la même chose dans Visual Studio.

#### <a name="title-bars"></a>Barres de titre

- Le texte dans la barre de titre doit refléter le nom de la commande qui l’a lancé.

- Aucune icône ne doit être utilisé dans les barres de titre de boîte de dialogue. Dans les cas où le système nécessite un, utilisez le logo de Visual Studio.

- Boîtes de dialogue ne doivent pas avoir réduite ou augmentée de boutons.

- Boutons d’aide dans la barre de titre ont été déconseillées. N’ajoutez pas les nouvelles boîtes de dialogue. Lorsqu’ils n’existent pas, ils doivent lancer une rubrique d’aide sur le plan conceptuel correspondant à la tâche.

  ![Spécifications des indications pour les barres de titre des boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Spécifications des indications pour les barres de titre des boîtes de dialogue Visual Studio

#### <a name="control-buttons"></a>Boutons de contrôle
En règle générale, **OK**, **Annuler**, et **aide** boutons doivent être organisés horizontalement dans le coin inférieur droit de la boîte de dialogue. L’autre pile verticale est autorisée si une boîte de dialogue comporte plusieurs autres boutons en bas de la boîte de dialogue qui présente visual toute confusion avec les boutons de contrôle.

![Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio

La boîte de dialogue doit inclure un bouton de contrôle par défaut. Pour déterminer la meilleure commande à utiliser en tant que la valeur par défaut, choisissez parmi les options suivantes (répertoriées par ordre de priorité) :

-   Choisissez la commande plus sûre et plus sûre en tant que la valeur par défaut. Cela signifie en choisissant la commande susceptible d’empêcher la perte de données et accès au système involontaire.

-   Si la sécurité et perte de données ne sont pas des facteurs, puis choisissez la commande par défaut basée sur plus de commodité. Y compris la commande la plus probable en tant que la valeur par défaut améliore les flux de travail de l’utilisateur lorsque la boîte de dialogue prend en charge des tâches fréquentes ou répétitives.

Évitez de choisir une action destructrice définitivement pour la commande par défaut. Si une commande de ce type est présente, choisissez une commande plus sûre en tant que la valeur par défaut.

#### <a name="access-keys"></a>Touches d’accès rapide
N’utilisez pas les clés d’accès de **OK**, **Annuler**, ou **aide** boutons. Ces boutons sont mappés aux touches de raccourci par défaut :

| Nom du bouton | Raccourci clavier |
| --- | --- |
| OK | Entrée |
| Annuler | Échap |
| Aide | F1 |

#### <a name="imagery"></a>Imagery
Utilisez des images avec parcimonie dans les boîtes de dialogue. Ne pas utiliser de grandes icônes dans les boîtes de dialogue simplement pour utiliser l’espace. Utiliser des images uniquement si elles sont une partie importante de transmettre le message à l’utilisateur, telles que des icônes d’avertissement ou des animations d’état.

###  <a name="BKMK_PrioritizingAndLayering"></a> Définition des priorités et superposition

#### <a name="prioritizing-your-ui"></a>Priorités de votre interface utilisateur
Il peut être nécessaire de mettre certains éléments d’interface utilisateur au premier plan et placer le comportement plus avancée et les options (y compris les commandes obscurs) dans les boîtes de dialogue. Mettez les fonctionnalités couramment utilisées au premier plan en place pour celui-ci et en le rendant visible par défaut dans l’interface utilisateur avec une étiquette de texte lorsque la boîte de dialogue s’affiche.

#### <a name="layering-your-ui"></a>Superposition de votre interface utilisateur
Si vous avez déterminé qu’une boîte de dialogue n’est nécessaire, mais les fonctionnalités associées que vous souhaitez présenter à l’utilisateur va au-delà de ce qui peut être affiché dans une boîte de dialogue simple, vous devez la couche de votre interface utilisateur. Les méthodes les plus courantes de superposition qu'utilise Visual Studio sont des onglets et des couloirs ou des tableaux de bord. Dans certains cas, les régions que vous peuvent développer et réduire peuvent convenir. Interface utilisateur adaptative n’est généralement pas recommandé dans Visual Studio.

Présente des avantages et inconvénients des différentes méthodes de superposition de l’interface utilisateur via des contrôles onglet. Passez en revue la liste ci-dessous pour vous assurer que vous choisissez une technique de superposition qui convient à votre situation.

##### <a name="tabbing"></a>Tabulation

| Mécanisme de commutation | Avantages et l’utilisation appropriée | Utilisation inappropriée et des inconvénients |
| --- | --- | --- |
| Contrôle Tab | Regrouper logiquement des pages de la boîte de dialogue dans les ensembles liés<br /><br />Utile pour moins de cinq (ou le nombre d’onglets qui tiennent dans une ligne dans la boîte de dialogue) pages de contrôles connexes dans la boîte de dialogue<br /><br />Onglet étiquettes doivent être courts : un ou deux mots qui peuvent identifier facilement le contenu<br /><br />Un style de boîte de dialogue système commun<br /><br />Exemple : **Explorateur de fichiers &gt; propriétés d’un élément** | Étiquettes courts descriptifs peut s’avérer<br /><br />En règle générale n’évolue pas au-delà de cinq onglets dans une boîte de dialogue<br /><br />Inapproprié si vous avez trop d’onglets pour une ligne (utilisez une technique alternative superposition)<br /><br />Pas extensible. |
| Navigation avec barre latérale | Périphérique de commutation simple pouvant s’adapter à plusieurs catégories à onglets<br /><br />Liste plate de catégories (aucune hiérarchie)<br /><br />Extensible<br /><br />Exemple : **Personnaliser... &gt; Ajouter des commandes** | Pas un bon usage d’espace horizontal s’il existe moins de trois groupes<br /><br />Tâche peut être mieux adaptée à une liste déroulante. |
| Contrôle Tree | Permet de catégories illimités<br /><br />Permet le regroupement et/ou de la hiérarchie de catégories<br /><br />Extensible<br /><br />Exemple : **Outils &gt; Options** | Hiérarchies fortement imbriquées peuvent entraîner un défilement horizontal excessive<br /><br />Visual Studio a un overabundance de vues de l’arborescence |
| Assistant | Permet à la fin de la tâche à guider l’utilisateur à travers les étapes séquentielles, basé sur des tâches : l’Assistant représente une tâche de haut niveau et les panneaux individuels représentent les tâches subordonnées nécessaires pour accomplir la tâche globale<br /><br />Utile lorsque la tâche traverse les limites de l’interface utilisateur, comme lorsque l’utilisateur auriez à utiliser plusieurs éditeurs et fenêtres pour terminer la tâche d’outil<br /><br />Utile lors de la tâche nécessite la création de branches<br /><br />Utile lors de la tâche contient des dépendances entre les étapes<br /><br />Utile lorsque plusieurs tâches similaires avec la branche d’une décision peuvent être présentés dans une boîte de dialogue pour réduire le nombre de différentes boîtes de dialogue similaire | Inapproprié pour n’importe quelle tâche qui ne nécessite pas un workflow séquentiel<br /><br />Les utilisateurs peuvent être submergée et confondues par un Assistant avec de trop nombreuses étapes<br /><br />Assistants sont limitée, par nature, écran |

##### <a name="hallways-or-dashboards"></a>Couloirs ou des tableaux de bord
Couloirs et tableaux de bord est des boîtes de dialogue ou les panneaux qui servent de lancement des points vers d’autres boîtes de dialogue et le windows. Le « couloir » bien conçu fait apparaître immédiatement uniquement les plus courants options, commandes et paramètres, ce qui permet de l’utilisateur de facilement accomplir des tâches courantes. Comme un couloir réalistes fournit guichets pour accéder aux salles de derrière, ici l’interface utilisateur moins courantes est collectée dans distinct « locaux » (souvent autres boîtes de dialogue) de fonctionnalités connexes qui sont accessibles à partir du couloir principal.

Vous pouvez également une interface utilisateur qui offre toutes les fonctionnalités disponibles dans une collection unique plutôt que la fonctionnalité moins courantes dans des emplacements distincts de refactorisation est simplement un tableau de bord.

![Concept de couloir pour exposer une interface utilisateur supplémentaire dans Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concept de couloir pour exposer une interface utilisateur supplémentaire dans Outlook

##### <a name="adaptive-ui"></a>Interface utilisateur adaptative
Affichage ou masquage de l’interface utilisateur basée sur l’utilisation ou expérience automatique signalés d’un utilisateur est une autre façon de présenter l’interface utilisateur nécessaire tout en masquant les autres parties. Cela n’est pas recommandé dans Visual Studio, comme les algorithmes pour déterminer à quel moment afficher ou masquer l’interface utilisateur peuvent être difficile, et les règles ne sera toujours incorrect pour un jeu de cas.

##  <a name="BKMK_Projects"></a> Projets

### <a name="projects-in-the-solution-explorer"></a>Projets dans l’Explorateur de solutions
La plupart des projets sont classés en fonction de référence, basée sur le répertoire ou mixte. Les trois types de projets sont prises en charge simultanément dans l’Explorateur de solutions. La racine de l’expérience utilisateur dans l’utilisation de projets s’effectue à l’intérieur de cette fenêtre. Bien que les nœuds de projet différents sont référence, répertoire ou projets en mode mixte, il est un modèle d’interaction commun qui doit être appliqué comme point de départ avant divergence des modèles spécifiques au projet utilisateur.

Projets doivent toujours :

-   Prise en charge la possibilité d’ajouter des dossiers pour organiser le contenu du projet du projet

-   Mettre à jour un modèle cohérent pour la persistance d’un projet

Projets doivent également conserver des modèles d’interaction cohérente pour :

-   Suppression d’éléments de projet

-   Enregistrer des documents

-   Modification des propriétés de projet

-   Modifier le projet dans une autre vue

-   Opérations de glisser-déplacer

### <a name="drag-and-drop-interaction-model"></a>Modèle d’interaction de glisser-déplacer
Projets classifier généralement eux-mêmes en tant que base de référence (en mesure de conserver uniquement les références aux éléments de projet dans le stockage), (en mesure de conserver les éléments de projet uniquement physiquement stockées au sein de la hiérarchie d’un projet), basée sur directory ou mixte (capable de conserver des références ou éléments physiques). L’IDE prend en charge les trois types de projets simultanément dans le **l’Explorateur de solutions**.

À partir d’un point de vue de glisser-déplacer, les caractéristiques suivantes doivent s’appliquer à chaque type de projet au sein de la **l’Explorateur de solutions**:

-   **Projet de référence :** Le point essentiel est que le projet fait glisser autour d’une référence à un élément dans le stockage. Lorsqu’un projet basé sur la référence agit comme une source pour une opération de déplacement, il doit supprimer uniquement la référence à l’élément à partir du projet. L’élément ne doit pas réellement supprimé du disque dur. Lorsqu’un projet basé sur la référence agit comme une cible pour une opération de déplacement (ou copie), il doit ajouter une référence à l’élément source d’origine sans avoir à effectuer une copie privée de l’élément.

-   **Basé sur le répertoire de projet :** Du point de vue du glisser-déplacer, le projet fait glisser autour de l’élément physique plutôt qu’une référence. Lorsqu’un projet basé sur le répertoire agit comme une source pour une opération de déplacement, il doit se terminer si vous supprimez l’élément physique du disque dur, ainsi que de supprimer du projet. Lorsqu’un projet basé sur le répertoire agit comme une cible pour une opération de déplacement (ou copie), il doit être une copie de l’élément source dans son emplacement cible.

-   **Projet cible mixte :** Du point de vue du glisser-déplacer, le comportement de ce type de projet est basé sur la nature de l’élément déplacé (il s’agit d’une référence à un élément dans le stockage) ou l’élément lui-même. Le comportement correct des références et les éléments physiques sont décrits ci-dessus.

S’il n'agissait qu’un seul type de projet dans le **l’Explorateur de solutions**, les opérations de glisser-déplacer est simples. Étant donné que chaque système de projet a la possibilité de définir son propre comportement de glisser-déplacer, vous devraient suivre certaines règles (en fonction du comportement de glisser-déplacer de l’Explorateur Windows) pour garantir une expérience utilisateur prévisible :

-   Opération glisser un non modifié le **l’Explorateur de solutions** (lorsque ni Ctrl ni les touches MAJ sont maintenu enfoncé) doit aboutir à une opération de déplacement.

-   L’opération de glissement de décalage doit également aboutir à une opération de déplacement.

-   L’opération de glissement-CTRL doit aboutir à une opération de copie.

-   Systèmes de projet en fonction de référence et mixte prennent en charge la notion d’ajout d’un lien (ou référence) à l’élément source. Lorsque ces projets sont la cible d’une opération de glisser-déplacer (lorsque **Ctrl + Maj** est maintenu enfoncé), il doit entraîner une référence à l’élément ajouté au projet

Toutes les opérations de glisser-déplacer sont cohérent entre les combinaisons de projets basée sur une référence basée sur le répertoire et mixtes. En particulier, il est problématique de prétendre à autoriser une opération de déplacement entre une source basée sur le répertoire de projet et cible en fonction de référence, car le projet source directory aura supprimer l’élément source à l’achèvement du déplacement. Le projet référence cible puis finiriez avec une référence à un élément supprimé.

Il est également trompeur de se faire passer pour autoriser une opération de copie entre ces types de projets, car le projet de base de référence cible n’effectuez pas une copie indépendante de l’élément source. De même, Ctrl + Maj en faisant glisser vers un projet basé sur le répertoire de la cible ne doit pas être autorisé, car un projet basé sur le répertoire ne peut pas conserver les références. Dans les cas où l’opération de glisser-déplacer n’est pas pris en charge, l’IDE doit interdire la suppression et afficher l’utilisateur le curseur de non-déplacement (indiqué dans le tableau de pointeur ci-dessous).

Pour implémenter correctement un comportement de glisser-déplacer, le projet source de l’opération glisser doit communiquer sa nature dans le projet cible. (Par exemple, est-il en fonction de référence ou de répertoire ?) Cette information est indiquée par le format de Presse-papiers qui est proposé par la source. Comme la source de glissement (ou opération de copie du Presse-papiers) un projet doit offrir `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS` respectivement, selon si le projet est basée sur le répertoire ou référence. Les deux de ces formats ont le même contenu de données, ce qui est similaire à la Windows `CF_HDROP` mettre en forme, à ceci près que les listes de chaînes, au lieu d’être des noms de fichiers, sont un double -`NULL` s’est arrêté de liste de `Projref` chaînes (tel que retourné par `IVsSolution::GetProjrefOfItem`ou `::GetProjrefOfProject` selon le cas).

La cible d’une liste (ou une opération de collage du Presse-papiers), un projet doit accepter tous les deux `CF_VSREFPROJECTITEMS` et `CF_VSSTGPROJECTITEMS`, bien que la gestion exacte de l’opération de glisser-déplacer varie selon la nature du projet cible et le projet source. Le projet source déclare sa nature par si elle offre `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS`. La cible de la liste déroulante comprend ses propres nature et a donc suffisamment d’informations pour prendre des décisions en tant que pour qu’elles soient un déplacement, la copie, ou lien doit être effectué. L’utilisateur modifie également quelle opération de glisser-déplacer doit être effectuée en appuyant sur Ctrl, MAJ, ou à la fois Ctrl et MAJ enfoncées. Il est important pour la cible de dépôt pour correctement indiquer quelle opération sera effectuée à l’avance dans son `DragEnter` et `DragOver` méthodes. Le **l’Explorateur de solutions** détermine automatiquement si le projet source et le projet cible sont le même projet.

En faisant glisser des éléments de projet entre les instances de Visual Studio (par exemple, à partir d’une instance de devenv.exe à un autre) n’est pas non plus pris en charge. Le **l’Explorateur de solutions** également directement désactive cela.

L’utilisateur doit toujours être en mesure de déterminer l’effet d’une opération de glisser-déplacer en sélectionnant un élément, faites-la glisser vers l’emplacement cible et en observant parmi les pointeurs de souris suivant s’affiche avant la suppression de l’élément :

| Pointeur de la souris | Commande | Description |
| :---: | --- | --- |
| ![Icône de « aucun dépôt » de la souris](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Aucun dépôt | Élément ne peut pas être déposé à l’emplacement spécifié. |
| ![Icône de « copie » de la souris](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copier | Élément sera copié vers l’emplacement cible. |
| ![Icône de souris « déplacer »](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Déplacement | Élément sera déplacé vers l’emplacement cible. |
| ![Icône de souris « ajouter une référence »](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Ajouter une référence | Une référence à l’élément sélectionné est ajoutée à l’emplacement cible. |

#### <a name="reference-based-projects"></a>Projets basés sur une référence
 Le tableau suivant récapitule les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets de la cible en fonction référencée :

| Modificateur | Catégorie | Élément de la source : Référence/lien | Élément de la source : Système d’élément ou le fichier physique (`CF_HDROP`) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacement | Link |
| Aucun modificateur | Cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Conserve l’élément d’origine |
| Aucun modificateur | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Maj + faire glisser | Action | Déplacement | Aucun dépôt |
| Maj + faire glisser | Cible | Ajoute la référence à l’élément d’origine | Aucun dépôt |
| Maj + faire glisser | Source | Référence de suppressions à l’élément d’origine | Aucun dépôt |
| Maj + faire glisser | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | Aucun dépôt |
| Ctrl+Drag | Action | Copier | Aucun dépôt |
| Ctrl+Drag | Cible | Ajoute la référence à l’élément d’origine | Aucun dépôt |
| Ctrl+Drag | Source | Conserve la référence à l’élément d’origine | Aucun dépôt |
| Ctrl+Drag | Résultat | `DROPEFFECT_COPY` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | Aucun dépôt |
| Ctrl + Maj + faire glisser | Action | Link | Link |
| Ctrl + Maj + faire glisser | Cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |
| Ctrl + Maj + faire glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + Maj + faire glisser | Résultat | `DROPEFFECT_LINK` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Ctrl + Maj + faire glisser | Remarque | Identique au comportement de glisser-déplacer pour les raccourcis dans l’Explorateur Windows. ||
| Couper/coller | Action | Déplacement | Link |
| Couper/coller | Cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |
| Couper/coller | Source | Conserve la référence à l’élément d’origine|Conserve l’élément d’origine |
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Link |
| Copier/coller | Source | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |
| Copier/coller | Résultat | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Action | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |

#### <a name="directory-based-projects"></a>Projets basés sur le répertoire
Le tableau suivant résume les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets de cible basé sur le répertoire :


| Modificateur | Catégorie | Élément de la source : Référence/lien | Élément de la source : Système d’élément ou le fichier physique (`CF_HDROP`) |
|-----------------|----------| - | - |
| Aucun modificateur | Action | Déplacement | Déplacement |
| Aucun modificateur | Cible | Élément de copie à l’emplacement cible | Élément de copie à l’emplacement cible |
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Référence de suppressions à l’élément d’origine |
| Maj + faire glisser | Action | Déplacement | Déplacement |
| Maj + faire glisser | Cible | Élément de copie à l’emplacement cible | Élément de copie à l’emplacement cible |
| Maj + faire glisser | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Maj + faire glisser | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Ctrl+Drag | Action | Copier | Copier |
| Ctrl+Drag | Cible | Élément de copie à l’emplacement cible | Élément de copie à l’emplacement cible |
| Ctrl+Drag | Source | Conserve la référence à l’élément d’origine | Conserve la référence à l’élément d’origine |
| Ctrl+Drag | Résultat | `DROPEFFECT_COPY` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_COPY` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Ctrl + Maj + faire glisser | | Aucun dépôt | Aucun dépôt |
| Couper/coller | Action | Déplacement | Déplacement |
| Couper/coller | Cible | Élément de copie à l’emplacement cible | Élément de copie à l’emplacement cible |
| Couper/coller | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément est supprimé de l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Copier |
| Copier/coller | Cible | Ajoute la référence à l’élément d’origine | Élément de copie à l’emplacement cible |
| Copier/coller | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans le stockage d’ins l’emplacement d’origine |

#### <a name="mixed-target-projects"></a>Projets cibles mixte
Le tableau suivant résume les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets cibles mixte :

| Modificateur | Catégorie | Élément de la source : Référence/lien | Élément de la source : Système d’élément ou le fichier physique (`CF_HDROP`) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacement | Déplacement |
| Aucun modificateur | Cible | Ajoute la référence à l’élément d’origine | Élément de copie à l’emplacement cible |
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Référence de suppressions à l’élément d’origine |
| Aucun modificateur | Résultat | `DROPEFFECT_ MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Maj + faire glisser | Action | Déplacement | Déplacement |
| Maj + faire glisser | Cible | Ajoute la référence à l’élément d’origine | Élément de copie à l’emplacement cible |
| Maj + faire glisser | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Maj + faire glisser | Résultat | `DROPEFFECT_ MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action à partir de `::Drop` et de l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Ctrl+Drag | Action | Copier | Copier |
| Ctrl+Drag | Cible | Ajoute la référence à l’élément d’origine | Élément de copie à l’emplacement cible |
| Ctrl+Drag | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl+Drag | Résultat | `DROPEFFECT_ COPY` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ COPY` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Ctrl + Maj + faire glisser | Action | Link | Link |
| Ctrl + Maj + faire glisser | Cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément source d’origine |
| Ctrl + Maj + faire glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + Maj + faire glisser | Résultat | `DROPEFFECT_ LINK` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ LINK` est retourné en tant qu’action à partir de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Couper/coller | Action | Déplacement | Déplacement |
| Couper/coller | Cible | Élément de copie à l’emplacement cible | Élément de copie à l’emplacement cible |
| Couper/coller | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément est supprimé de l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Copier |
| Copier/coller | Cible | Ajoute la référence à l’élément d’origine | Élément de copie à l’emplacement cible |
| Copier/coller | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |

Ces détails doivent être prises en considération lors de l’implémentation en faisant glisser le **l’Explorateur de solutions**:

-   Conception pour plusieurs scénarios de sélection.

-   Noms de fichier (chemin d’accès complet) doivent être uniques dans le projet cible ou la liste ne doit pas être autorisée.

-   Les noms de dossier doivent être uniques (non-respect de la casse) au niveau qu’ils sont en cours de suppression.

-   Il existe des différences de comportement entre les fichiers qui sont ouverts ou fermés au moment de glisser (non mentionnée dans les scénarios ci-dessus).

-   Fichiers de niveau supérieur se comportent différemment des fichiers des dossiers.

Un autre problème à connaître est comment gérer les opérations de déplacement des éléments qui ont des éditeurs ou les concepteurs ouverts. Le comportement attendu est comme suit (cela s’applique à tous les types de projet) :

1.  Si l’éditeur ouvrir/le concepteur n’a pas les modifications non enregistrées, la fenêtre d’éditeur/concepteur doit être fermée en mode silencieux.

2.  Si l’éditeur ouvrir/le concepteur n’a pas les modifications non enregistrées, la source de l’opération glisser doit attendre pour la suppression se produire et demandez à l’utilisateur pour enregistrer les modifications non validées dans les documents ouverts avant de fermer la fenêtre avec une invite semblable à ce qui suit :

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Ainsi, l’utilisateur l’opportunité d’enregistrer le travail en cours avant la cible met ses copies. Une nouvelle méthode `IVsHierarchyDropDataSource2::OnBeforeDropNotify` a été ajoutée pour permettre cette gestion.

La cible de copie de l’état de l’élément car il s’agit dans le stockage (sans les modifications non enregistrées dans l’éditeur si l’utilisateur a choisi **non**). Une fois la cible a terminé sa copie (dans `IVsHierarchyDropDataSource::Drop`), la source est la possibilité pour terminer la partie de la suppression de l’opération de déplacement (dans `IVsHierarchyDropDataSource::OnDropNotify`).

Les éditeurs sans enregistrer les modifications doivent être laissées ouverts. Pour ces documents avec les modifications non enregistrées, cela signifie que la partie de la copie de l’opération de déplacement sera effectuée, mais la partie de la suppression va être abandonnée. Dans un scénario de sélection de plusieurs quand l’utilisateur choisit **non**, ces documents avec des modifications non enregistrées ne doivent pas être fermés ou supprimés, mais celles sans modifications non enregistrées doivent être fermés et supprimés.
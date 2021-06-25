---
title: Modèles d’application pour Visual Studio | Microsoft Docs
description: Découvrez la différence entre les fenêtres de document, les fenêtres outil et les boîtes de dialogue non modales, y compris les modèles d’utilisation de fenêtre pour les nouvelles fonctionnalités de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2726c7096bbf4606fbab2c32b01ffd197549e13c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899184"
---
# <a name="application-patterns-for-visual-studio"></a>Modèles d’application pour Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interactions entre les fenêtres

### <a name="overview"></a>Vue d’ensemble
Les deux types de fenêtre principaux utilisés dans Visual Studio sont les éditeurs de documents et les fenêtres outil. Les boîtes de dialogue non modales sont rares, mais possibles. Bien qu’elles soient toutes non modales dans le shell, leurs modèles sont fondamentalement différents. Cette section décrit la différence entre les fenêtres de document, les fenêtres outil et les boîtes de dialogue non modales. Les boîtes de dialogue modales sont traitées dans les [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparaison des modèles d’utilisation de fenêtre
Les **fenêtres de document** sont presque toujours affichées dans la barre des documents. Cela donne à l’éditeur de document une « phase centrale » pour organiser les fenêtres d’outils supplémentaires autour.

Une **fenêtre outil** s’affiche le plus souvent sous la forme d’une fenêtre distincte, plus petite et réduite au bord de l’IDE. Cela peut être visible, masqué ou masqué automatiquement. Toutefois, parfois, les fenêtres outil sont présentées dans le document, en dévérifiant la propriété **fenêtre/ancrage** dans la fenêtre. Cela aboutit à une plus grande surface, mais également à une décision de conception courante : quand vous tentez de l’intégrer dans Visual Studio, vous devez décider si votre fonctionnalité doit afficher une fenêtre outil ou une fenêtre de document.

Les **boîtes de dialogue non modales** sont déconseillées dans Visual Studio. La plupart des boîtes de dialogue non modales sont, par définition, des fenêtres outil flottantes et doivent être implémentées de cette façon. Les boîtes de dialogue non modales sont autorisées dans les cas où la taille d’une fenêtre outil normale ancrée sur le côté de l’interpréteur de commandes serait trop limitative. Ils sont également autorisés dans les cas où l’utilisateur est susceptible de déplacer la boîte de dialogue vers un moniteur secondaire.

Réfléchissez bien au type de conteneur dont vous avez besoin. Les considérations courantes relatives au modèle d’utilisation pour la conception de l’interface utilisateur sont répertoriées dans le tableau suivant.

||Fenêtre de document|Fenêtre outil|Boîte de dialogue non modale|
|-|---------------------|-----------------|---------------------|
| **Position** | Toujours positionné dans le même document et n’est pas ancré autour des bords de l’IDE. Elle peut être « extraite » pour qu’elle flotte séparément de l’interpréteur de commandes principal. | Généralement, les onglets sont ancrés autour des bords de l’IDE, mais ils peuvent être personnalisés pour être flottants, masqués automatiquement (désépinglés) ou ancrés dans le même document.|Grande fenêtre flottante distincte de l’IDE. |
| **Valider le modèle** | *Validation différée*<br /><br /> Pour enregistrer les données dans un document, l’utilisateur doit émettre la commande **fichier &gt; Enregistrer**, **Enregistrer sous** ou **enregistrer tout** . Une fenêtre de document a le concept de données qui est « modifié », puis validé sur l’une des commandes d’enregistrement. Lors de la fermeture d’une fenêtre de document, tout le contenu est enregistré sur le disque ou perdu. | *Validation immédiate*<br /><br /> Il n’existe aucun modèle d’enregistrement. Pour les fenêtres outil de l’inspecteur qui aident à modifier un fichier, le fichier doit être ouvert dans l’éditeur ou le concepteur actif, et l’éditeur ou le concepteur est propriétaire de l’enregistrement. | *Validation différée ou immédiate*<br /><br /> La plupart du temps, une boîte de dialogue non modale nécessite une action pour valider les modifications et permet une opération d’annulation, qui annule toutes les modifications apportées dans la session de dialogue.  Cela fait la différence entre une boîte de dialogue non modale et une fenêtre outil dans laquelle les fenêtres outil disposent toujours d’un modèle de validation immédiate. |
| **Visibilité** | *Ouvrir/créer (fichier) et fermer*<br /><br /> Pour ouvrir une fenêtre de document, vous pouvez ouvrir un document existant ou utiliser un modèle pour créer un nouveau document. Il n’y a aucune \<specific editor> commande « ouvrir ». | *Masquer et afficher*<br /><br /> Les fenêtres outil à instance unique peuvent être masquées ou affichées. Le contenu et les États au sein de la fenêtre outil sont rendus persistants en vue ou masqués. Les fenêtres outil multi-instances peuvent être fermées et masquées. Quand une fenêtre outil à instances multiples est fermée, le contenu et l’état de la fenêtre outil sont ignorés. | *Lancé à partir d’une commande*<br /><br /> Les boîtes de dialogue sont lancées à partir d’une commande basée sur des tâches. |
| **Instances** | *Multi-instance*<br /><br /> Plusieurs éditeurs peuvent être ouverts en même temps et en modifiant différents fichiers, tandis que certains éditeurs autorisent également l’ouverture du même fichier dans plusieurs éditeurs (à l’aide de la commande **fenêtre &gt; nouvelle fenêtre** ).<br /><br /> Un seul éditeur peut modifier un ou plusieurs fichiers en même temps (Concepteur de projets). | *Une seule ou plusieurs instances*<br /><br /> Le contenu change pour refléter le contexte (comme dans l’Explorateur de propriétés) ou le focus ou le contexte Push vers d’autres fenêtres (Liste des tâches, Explorateur de solutions).<br /><br /> Les fenêtres outil à instance unique et à instances multiples doivent être associées à la fenêtre de document active, à moins qu’il y ait une raison impérieuse de ne pas les utiliser. | *Instance unique* |
| **Exemples** | **Éditeurs de texte**, comme l’éditeur de code<br /><br /> Des **aires de conception**, comme un concepteur de formulaires ou une surface de modélisation<br /><br /> **Contrôler les dispositions similaires aux boîtes de dialogue**, comme le concepteur de manifeste | L' **Explorateur de solutions** fournit une solution et des projets contenus dans la solution.<br /><br /> L' **Explorateur de serveurs** fournit une vue hiérarchique des serveurs et des connexions de données que l’utilisateur choisit d’ouvrir dans la fenêtre. L’ouverture d’un objet à partir de la hiérarchie de la base de données, comme une requête, ouvre une fenêtre de document et permet à l’utilisateur de modifier la requête.<br /><br /> L' **Explorateur de propriétés** affiche les propriétés de l’objet sélectionné dans une fenêtre de document ou dans une autre fenêtre outil. Les propriétés sont présentées dans une vue de grille hiérarchique ou dans des contrôles de type dialogue complexes et permettent à l’utilisateur de définir les valeurs de ces propriétés. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Fenêtres outil

### <a name="overview"></a>Vue d’ensemble
Les fenêtres outil prennent en charge le travail de l’utilisateur qui se produit dans les fenêtres de document. Elles peuvent être utilisées pour afficher une hiérarchie qui représente un objet racine fondamental que Visual Studio fournit et peut manipuler.

Lorsque vous envisagez une nouvelle fenêtre outil dans l’IDE, les auteurs doivent :

- Utilisez des fenêtres outil appropriées à la tâche et n’en créez pas de nouvelles avec des fonctionnalités similaires. Les nouvelles fenêtres outil ne doivent être créées que si elles offrent un « outil » ou des fonctionnalités qui ne peuvent pas être intégrées dans une fenêtre similaire, ou en transformant une fenêtre existante en Hub pivotant.

- Utilisez une barre de commandes standard, si nécessaire, en haut de la fenêtre outil.

- Soyez cohérent avec les modèles déjà présents dans d’autres fenêtres outil pour le contrôle de la présentation et de la navigation au clavier.

- Soyez cohérent avec la présentation des contrôles dans d’autres fenêtres outil.

- Rendez les fenêtres d’outils spécifiques au document visibles automatiquement si possible, afin qu’elles apparaissent uniquement lorsque le document parent est activé.

- Vérifiez que le contenu de la fenêtre est navigable par le clavier (touches de direction de la prise en charge).

#### <a name="tool-window-states"></a>États de la fenêtre outil
Les fenêtres Outil Visual Studio ont des États différents, dont certains sont activés par l’utilisateur (par exemple, la fonctionnalité de masquage automatique). D’autres États, comme ceux qui sont visibles automatiquement, permettent aux fenêtres outil d’apparaître dans le contexte approprié et de les masquer lorsque cela n’est pas nécessaire. Il y a cinq États de fenêtre d’outils au total.

- Les fenêtres d’outils **ancrées/épinglées** peuvent être attachées à l’un des quatre côtés de la zone de document. L’icône de punaise apparaît dans la barre de titre de la fenêtre outil. La fenêtre outil peut être ancrée horizontalement ou verticalement le long du bord de l’interpréteur de commandes et d’autres fenêtres outil, et peut également être liée par tabulation.

- Les fenêtres outil **masquées automatiquement** sont désépinglées. La fenêtre peut être détourée, laissant un onglet (avec le nom de la fenêtre outil et son icône) sur le bord de la zone de document. La fenêtre outil disparaît lorsqu’un utilisateur pointe sur l’onglet.

- **Les** fenêtres outil visibles automatiquement apparaissent quand une autre partie de l’interface utilisateur, comme un éditeur, est lancée ou obtient le focus.

- Les fenêtres outil **flottantes** pointent en dehors de l’IDE. Cela est utile pour les configurations à plusieurs écrans.

- Les fenêtres outil de **document avec onglet** peuvent être ancrées dans le document. Cela est utile pour les fenêtres d’outils volumineuses, telles que l’Explorateur d’objets, qui nécessitent plus de place que l’ancrage aux bords du frame.

![États de la fenêtre Outil dans Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />États de la fenêtre Outil dans Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instance unique et multi-instance
Les fenêtres outil sont de type instance unique ou multi-instance. Certaines fenêtres outil à instance unique peuvent être associées à la fenêtre de document active, alors que les fenêtres outil multi-instances peuvent ne pas l’être. Les fenêtres outil multi-instances répondent à la commande **fenêtre &gt; nouvelle fenêtre** en créant une nouvelle instance de la fenêtre. L’image suivante illustre une fenêtre outil qui active la commande nouvelle fenêtre lorsqu’une instance de la fenêtre est active :

![Fenêtre outil activant la commande’nouvelle fenêtre’lorsqu’une instance de la fenêtre est active](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Fenêtre outil activant la commande’nouvelle fenêtre’lorsqu’une instance de la fenêtre est active

Les fenêtres outil à instance unique peuvent être masquées ou affichées, tandis que les fenêtres outil multi-instances peuvent être fermées et masquées. Toutes les fenêtres Outil peuvent être ancrées, liées par tabulation, flottantes ou définies en tant que fenêtre enfant d’interface Multiple-Document (MDI) (similaire à une fenêtre de document). Toutes les fenêtres outil doivent répondre aux commandes de gestion de fenêtre appropriées dans le menu fenêtre :

![Commandes de gestion des fenêtres dans le menu fenêtre de Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Commandes de gestion des fenêtres dans le menu fenêtre de Visual Studio

#### <a name="document-specific-tool-windows"></a>Fenêtres outil spécifiques aux documents
Certaines fenêtres outil sont conçues pour changer en fonction d’un type de document donné. Ces mises à jour continues de Windows pour refléter les fonctionnalités applicables à la fenêtre de document active dans l’IDE.

Les exemples de fenêtres outil dont le contenu change pour refléter l’éditeur sélectionné sont la boîte à outils et la structure du document. Ces fenêtres affichent un filigrane lorsqu’un éditeur a le focus qui n’offre pas de contexte à la fenêtre.

#### <a name="navigable-list-tool-windows"></a>Fenêtres outil liste navigable
Certaines fenêtres d’outils affichent une liste d’éléments navigables avec lesquels l’utilisateur peut interagir. Dans ce type de fenêtre, il doit toujours y avoir un commentaire pour l’élément actuel dans la liste, même si la fenêtre est inactive. La liste doit répondre aux commandes **GoToNextLocation** et **GoToPrevLocation** en modifiant également l’élément actuellement sélectionné dans la fenêtre

Voici des exemples de fenêtres d’outils de liste navigable : Explorateur de solutions et la fenêtre résultats de la recherche.

### <a name="tool-window-types"></a>Types de fenêtre outil

#### <a name="common-tool-windows-and-their-functions"></a>Fenêtres d’outils courantes et leurs fonctions

**Fenêtres outil hiérarchiques**

| Fenêtre outil | Fonction |
| --- | --- |
| Explorateur de solutions | Arborescence hiérarchique qui affiche une liste de documents contenus dans des projets, des fichiers divers et des éléments de solution. L’affichage des éléments dans les projets est défini par le package qui possède le type de projet (par exemple, des types basés sur des références, des répertoires ou des modes mixtes). |
| Affichage de classes | Arborescence hiérarchique des classes et des différents éléments de la plage de travail des documents, indépendamment des fichiers eux-mêmes. |
| Explorateur de serveurs | Arborescence hiérarchique qui affiche tous les serveurs et connexions de données dans la solution. |
| Structure du document | Structure hiérarchique du document actif. |

**Fenêtres outil grille**

| Fenêtre outil | Fonction |
| --- | --- |
| Propriétés | Grille qui affiche une liste de propriétés pour l’objet sélectionné, ainsi que des sélecteurs de valeurs pour modifier ces propriétés. |
| Liste des tâches | Grille permettant à l’utilisateur de créer/modifier/supprimer des tâches et des commentaires. |

**Fenêtres outil de contenu**

| Fenêtre outil | Fonction |
| --- | --- |
| Aide | Une fenêtre qui permet aux utilisateurs d’accéder à différentes méthodes d’obtention d’aide, à partir de la section « Comment faire ? » vidéos sur les forums MSDN. |
| Aide dynamique | Fenêtre outil qui affiche des liens vers les rubriques d’aide applicables à la sélection actuelle. |
| Explorateur d'objets | Un jeu de frames à deux colonnes avec une liste de composants d’objets hiérarchiques dans le volet gauche et les propriétés et méthodes de l’objet dans la colonne de droite. |

**Fenêtres d’outils de dialogue**

| Fenêtre outil | Fonction |
| --- | --- |
| Rechercher | Boîte de dialogue qui permet à l’utilisateur de rechercher ou de rechercher et de remplacer dans différents fichiers de la solution. |
| Recherche avancée | Boîte de dialogue qui permet à l’utilisateur de rechercher ou de rechercher et de remplacer dans différents fichiers de la solution. |

**Autres fenêtres outil**

::: moniker range="vs-2017"

| Fenêtre outil | Fonction |
| --- | --- |
| Boîte à outils | Fenêtre outil utilisée pour stocker des éléments qui seront déposés sur des surfaces de conception, fournissant une source de glissement cohérente pour tous les concepteurs. |
| Page de démarrage | Le portail de l’utilisateur vers Visual Studio, avec accès aux flux des actualités des développeurs, à l’aide de Visual Studio et aux projets récents. Les utilisateurs peuvent également créer des pages de démarrage personnalisées en copiant le fichier StartPage. Xaml à partir du répertoire « Common7\IDE\StartPages \" Visual Studio Program Files » dans le dossier StartPages du répertoire de documents Visual Studio, puis en modifiant le code XAML manuellement ou en l’ouvrant dans Visual Studio ou dans un autre éditeur de code. |

::: moniker-end

::: moniker range=">=vs-2019"

| Fenêtre outil | Fonction |
| --- | --- |
| Boîte à outils | Fenêtre outil utilisée pour stocker des éléments qui seront déposés sur des surfaces de conception, fournissant une source de glissement cohérente pour tous les concepteurs. |

::: moniker-end

**Fenêtres outil du débogueur**

| Fenêtre outil | Fonction |
| --- | --- |
| Autos ||
| Immédiat ||
| Sortie | La fenêtre sortie peut être utilisée chaque fois que vous avez des événements textuels ou un État à déclarer. |
| Mémoire ||
| Points d’arrêt ||
| Exécution en cours ||
| Documents ||
| Pile des appels ||
| Locals ||
| Regarde ||
| Code Machine ||
| Registres ||
| Threads ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Conventions de l’éditeur de document

### <a name="document-interactions"></a>Interactions de documents
La « bonne partie du document » est l’espace le plus grand au sein de l’IDE et est l’endroit où l’utilisateur a généralement concentré son attention afin d’effectuer ses tâches, avec les fenêtres d’outils supplémentaires. Les éditeurs de documents représentent les unités de travail fondamentales que l’utilisateur ouvre et enregistre dans Visual Studio. Ils conservent un sens élevé de la sélection liée à Explorateur de solutions ou à d’autres fenêtres de hiérarchie actives. L’utilisateur doit pouvoir pointer vers l’une de ces fenêtres de hiérarchie et savoir où se trouve le document et sa relation avec la solution, le projet ou un autre objet racine fourni par un package Visual Studio.

La modification des documents nécessite une expérience utilisateur cohérente. Pour permettre à l’utilisateur de se concentrer sur la tâche à la main plutôt que sur la gestion des fenêtres et la recherche de commandes, sélectionnez une stratégie de vue de document qui correspond le mieux aux tâches utilisateur pour la modification de ce type de document.

#### <a name="common-interactions-for-the-document-well"></a>Interactions courantes pour la barre d’outils document

- Conservez un modèle d’interaction cohérent dans le **nouveau fichier** commun et ouvrez les expériences de **fichier** .

- Met à jour les fonctionnalités associées dans les fenêtres et les menus connexes lorsque la fenêtre de document s’ouvre.

- Les commandes de menu sont correctement intégrées à des menus courants tels que les menus **Edition**, **format** et **affichage** . Si un grand nombre de commandes spécialisées sont disponibles, vous pouvez créer un nouveau menu. Ce nouveau menu doit être visible uniquement lorsque le document a le focus.

- Une barre d’outils incorporée peut être placée en haut de l’éditeur. Il est préférable d’avoir une barre d’outils distincte qui s’affiche en dehors de l’éditeur.

- Conservez toujours une sélection dans la Explorateur de solutions ou dans une fenêtre de hiérarchie Active similaire.

- Le double-clic sur un document dans le Explorateur de solutions doit effectuer la même action que celle **ouverte**.

- Si plusieurs éditeurs peuvent être utilisés sur un type de document, l’utilisateur doit être en mesure de remplacer ou de réinitialiser l’action par défaut sur un type de document donné à l’aide de la boîte de dialogue **Ouvrir avec** en cliquant avec le bouton droit sur le fichier et en sélectionnant **Ouvrir avec** dans le menu contextuel.

- Ne créez pas un assistant dans un document.

### <a name="user-expectations-for-specific-document-types"></a>Attentes de l’utilisateur pour les types de documents spécifiques
Il existe plusieurs types de base d’éditeurs de documents et chacun d’eux a un ensemble d’interactions qui sont cohérentes avec d’autres types du même type.

- **Éditeur de texte :** éditeur de code, fichiers journaux

- **Aire de conception :** Concepteur de formulaires WPF, Windows Forms

- **Éditeur de style de boîte de dialogue :** Concepteur de manifeste, propriétés de projet

- **Générateur de modèles :** concepteur de flux de travail, codemap, diagramme d’architecture, progression

Il existe également plusieurs types non-éditeur qui utilisent la bien de document. Bien qu’ils ne modifient pas eux-mêmes les documents, ils doivent suivre les interactions standard pour les fenêtres de document.

- **Rapports :** Rapport IntelliTrace, rapport Hyper-V, rapport du profileur

- **Tableau de bord :** Hub de diagnostic

#### <a name="text-based-editors"></a>Éditeurs de texte

- Le document participe au modèle d’onglet d’aperçu, ce qui permet d’afficher un aperçu du document sans l’ouvrir.

- La structure du document peut être représentée dans une fenêtre d’outil complémentaire, telle qu’une structure de document.

- IntelliSense (le cas échéant) se comporte de manière cohérente avec d’autres éditeurs de code.

- Les fenêtres contextuelles ou l’interface utilisateur d’assistance suivent des styles et des modèles similaires pour une interface utilisateur similaire existante, par exemple CodeLens.

- Les messages relatifs à l’état du document s’affichent dans un contrôle de barre d’informations en haut du document ou dans la barre d’État.

- L’utilisateur doit être en mesure de personnaliser l’apparence des polices et des couleurs à l’aide d’une page **outils > options** , soit la page polices et couleurs partagées, soit une spécifique à l’éditeur.

#### <a name="design-surfaces"></a>Aires de conception

- Un concepteur vide doit avoir un filigrane sur l’aire indiquant comment commencer.

- Les mécanismes de basculement d’affichage suivent les modèles existants, tels que le double-clic pour ouvrir un éditeur de code ou les onglets de la fenêtre de document qui autorisent l’interaction avec les deux volets.

- L’ajout d’éléments à l’aire de conception doit être effectué via la boîte à outils, sauf si une fenêtre outil très spécifique est requise.

- Les éléments sur l’aire suivent un modèle de sélection cohérent.

- Les barres d’outils incorporées contiennent uniquement des commandes spécifiques aux documents, et non des commandes courantes telles que **Enregistrer**.

#### <a name="dialog-style-editors"></a>Éditeurs de style boîte de dialogue

- La disposition du contrôle doit respecter les conventions de disposition de boîte de dialogue normales.

- Les onglets de l’éditeur ne doivent pas correspondre à l’apparence des onglets de document, ils doivent correspondre à l’un des deux styles d’onglets intérieurs autorisés.

- Les utilisateurs doivent être en mesure d’interagir avec les contrôles à l’aide du clavier uniquement. soit en activant l’éditeur et en passant par des contrôles, soit en utilisant des mnémoniques standard.

- Le concepteur doit utiliser le modèle d’enregistrement commun. Aucun bouton d’enregistrement ou de validation global ne doit être placé sur l’aire de conception, bien que d’autres boutons soient appropriés.

#### <a name="model-designers"></a>Concepteurs de modèles

- Un concepteur vide doit avoir un filigrane sur l’aire indiquant comment commencer.

- L’ajout d’éléments à l’aire de conception doit être effectué via la boîte à outils.

- Les éléments sur l’aire suivent un modèle de sélection cohérent.

- Les barres d’outils incorporées contiennent uniquement des commandes spécifiques aux documents, et non des commandes courantes telles que **Enregistrer**.

- Une légende peut apparaître à l’aide d’un indicateur ou d’un filigrane.

- L’utilisateur doit être en mesure de personnaliser l’apparence des polices/couleurs à l’aide d’une page **outils > options** , soit la page polices et couleurs partagées, soit une spécifique à l’éditeur.

#### <a name="reports"></a>Rapports

- Les rapports sont généralement des informations uniquement et ne font pas partie du modèle d’enregistrement. Toutefois, ils peuvent inclure des interactions, telles que des liens vers d’autres informations ou sections pertinentes qui se développent et réduisent.

- La plupart des commandes sur l’aire de conception doivent être des liens hypertexte, et non des boutons.

- La disposition doit inclure un en-tête et suivre les instructions de mise en page de rapport standard.

#### <a name="dashboards"></a>Tableaux de bord

- Les tableaux de bord n’ont pas de modèle d’interaction proprement dit, mais servent de moyen d’offrir un large éventail d’autres outils.

- Ils ne participent pas au modèle d’enregistrement.

- Les utilisateurs doivent être en mesure d’interagir avec les contrôles à l’aide du clavier uniquement, soit en activant l’éditeur et en passant par les contrôles, soit en utilisant des mnémoniques standard.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Boîtes

### <a name="introduction"></a>Introduction
Dans Visual Studio, les boîtes de dialogue doivent généralement prendre en charge une unité discrète du travail de l’utilisateur, puis être fermée.

Si vous avez déterminé que vous avez besoin d’une boîte de dialogue, vous avez trois options, par ordre de préférence :

1. Intégrez vos fonctionnalités dans l’une des boîtes de dialogue partagées de Visual Studio.

2. Créez votre propre boîte de dialogue à l’aide d’un modèle trouvé dans une boîte de dialogue similaire existante.

3. Créez une boîte de dialogue, en suivant les instructions relatives à l’interaction et à la disposition.

Cette section explique comment choisir le modèle de boîte de dialogue correct dans les flux de travail Visual Studio et les conventions communes pour la conception de boîtes de dialogue.

### <a name="themes"></a>Thèmes
Les boîtes de dialogue de Visual Studio suivent l’un des deux styles de base suivants :

#### <a name="standard-unthemed"></a>Standard (pas à thème)
La plupart des boîtes de dialogue sont des boîtes de dialogue d’utilitaire standard et doivent être non-dépendantes. Ne remodèleez pas les contrôles communs et ne tentez pas de créer des boutons ou des contrôles « modernes » stylisés. Les contrôles et l’apparence [de chrome suivent les instructions d’interaction de bureau Windows standard pour les boîtes de dialogue](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>À thème
Les boîtes de dialogue « signature » de spécialité peuvent être à thème. Les boîtes de dialogue à thème ont une apparence distincte, qui comporte également des modèles d’interaction spéciaux associés au style. Thème votre boîte de dialogue uniquement si elle répond à ces exigences :

- La boîte de dialogue est une expérience courante qui sera affichée et utilisée souvent ou par de nombreux utilisateurs (par exemple, la boîte de dialogue **nouveau projet** .

- La boîte de dialogue contient des éléments de la même façon (par exemple, la boîte de dialogue **paramètres du compte** ).

- La boîte de dialogue apparaît en tant que partie intégrante d’un plus grand fluide qui comprend d’autres boîtes de dialogue à thème (par exemple, la boîte de dialogue **Ajouter un service connecté** ).

- La boîte de dialogue est une partie importante d’une expérience qui joue un rôle stratégique dans la promotion ou la différenciation d’une version de produit.

Lorsque vous créez une boîte de dialogue à thème, utilisez les couleurs d’environnement appropriées et suivez les modèles de disposition et d’interaction appropriés. (Consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Conception de dialogue
Les boîtes de dialogue bien conçues prennent en considération les éléments suivants :

- Tâche utilisateur prise en charge

- Le style, la langue et la terminologie du texte de la boîte de dialogue

- Choix des contrôles et conventions de l’interface utilisateur

- Spécification visuelle et alignement du contrôle

- Accès par le clavier

#### <a name="content-organization"></a>Organisation du contenu
Prenez en compte les différences entre ces types de dialogue de base :

- Les [boîtes de dialogue simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) présentent des contrôles dans une seule fenêtre modale. La présentation peut inclure des variations de modèles de contrôle complexes, y compris un sélecteur de champs ou une barre d’icône.

- Les [boîtes de dialogue en couches](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) sont utilisées pour tirer le meilleur parti de l’espace de l’écran lorsqu’un seul élément d’interface utilisateur comprend plusieurs groupes de contrôles. Les regroupements de la boîte de dialogue sont « superposés » via les contrôles onglet, les contrôles de liste de navigation ou les boutons afin que l’utilisateur puisse choisir le regroupement à afficher à un moment donné.

- Les [assistants](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sont utiles pour diriger l’utilisateur via une séquence logique d’étapes vers l’achèvement d’une tâche. Une série de choix est proposée dans des panneaux séquentiels, parfois en introduisant des flux de travail différents (« branches ») dépendants d’un choix effectué dans le panneau précédent.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Boîtes de dialogue simples
Une boîte de dialogue simple est une présentation de contrôles dans une seule fenêtre modale. Cette présentation peut inclure des variantes de modèles de contrôle complexes, tels qu’un sélecteur de champs. Pour les boîtes de dialogue simples, suivez la disposition générale standard, ainsi que toute disposition spécifique requise pour les regroupements de contrôles complexes.

![>créer une clé de nom fort est un exemple de boîte de dialogue simple dans Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Créer une clé de nom fort est un exemple de boîte de dialogue simple dans Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Boîtes de dialogue en couches
Les boîtes de dialogue en couches incluent des onglets, des tableaux de bord et des arborescences incorporées. Ils sont utilisés pour optimiser le volume de biens immobiliers lorsqu’il existe plusieurs groupes de contrôles proposés dans une seule et même interface utilisateur. Les regroupements sont superposés afin que l’utilisateur puisse choisir le regroupement à afficher à un moment donné.

Dans le cas le plus simple, le mécanisme de basculement entre les regroupements est un contrôle onglet. Plusieurs solutions sont disponibles. Pour savoir comment choisir le style le plus approprié, consultez hiérarchisation et structuration en couches.

La boîte de dialogue **&gt; Options des outils** est un exemple de boîte de dialogue en couches utilisant une arborescence incorporée :

![Outils > options est un exemple de boîte de dialogue en couches dans Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Outils > options est un exemple de boîte de dialogue en couches dans Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Assistants
Les assistants sont utiles pour diriger l’utilisateur via une séquence logique d’étapes dans l’exécution d’une tâche. Une série de choix est proposée dans des panneaux séquentiels, et l’utilisateur doit suivre chaque étape avant de passer à la suivante. Une fois que les valeurs par défaut disponibles sont suffisantes, le bouton **Terminer** est activé.

 Les assistants modaux sont utilisés pour les tâches qui :

- Contiennent des branchements, où différents chemins d’accès sont proposés en fonction des choix de l’utilisateur

- Contiennent des dépendances entre les étapes, où les étapes suivantes dépendent de l’entrée d’utilisateur de la ou des étapes précédentes

- Sont suffisamment complexes pour permettre l’utilisation de l’interface utilisateur pour expliquer les choix proposés et les résultats possibles à chaque étape

- Sont transactionnels, nécessitant l’exécution d’un ensemble d’étapes dans son intégralité avant que les modifications ne soient validées

### <a name="common-conventions"></a>Conventions courantes
Pour obtenir une conception et des fonctionnalités optimales avec vos boîtes de dialogue, suivez ces conventions sur la taille, la position, les normes, la configuration et l’alignement des contrôles, le texte de l’interface utilisateur, les barres de titre, les boutons de contrôle et les touches d’accès.

Pour obtenir des instructions spécifiques à la disposition, consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Taille
Les boîtes de dialogue doivent tenir dans une résolution d’écran minimale de 1024 x 768, et la taille de la boîte de dialogue initiale ne doit pas dépasser 900x700 pixels. Les boîtes de dialogue peuvent être redimensionnables, mais ce n’est pas une condition requise.

Il existe deux recommandations pour les boîtes de dialogue redimensionnables :

1. Qu’une taille minimale est définie pour la boîte de dialogue qui s’optimise pour le jeu de contrôles sans découpage, et s’adapte pour s’adapter à la croissance raisonnable de la localisation.

2. Que la taille mise à l’échelle par l’utilisateur est conservée d’une session à l’autres. Par exemple, si l’utilisateur met à l’échelle une boîte de dialogue à 150%, un lancement ultérieur de la boîte de dialogue s’affichera à 150%.

#### <a name="position"></a>Position
Les boîtes de dialogue doivent apparaître centrées dans l’IDE lors du premier lancement. La dernière position des boîtes de dialogue non redimensionnables n’a pas besoin d’être persistante, de sorte qu’elles apparaissent centrées lors des lancements suivants.

Pour les boîtes de dialogue redimensionnables, la taille doit être conservée lors des lancements suivants. Pour les boîtes de dialogue modales redimensionnables, la position n’a pas besoin d’être persistante. Leur affichage centré dans l’IDE permet d’éviter que la boîte de dialogue apparaisse dans une position imprévisible ou inutilisable lorsque la configuration d’affichage de l’utilisateur a changé.

Pour les boîtes de dialogue non modales qui peuvent être repositionnées, la position de l’utilisateur doit être conservée lors des lancements suivants, car la boîte de dialogue peut être utilisée fréquemment comme partie intégrante d’un flux de travail plus volumineux.

Lorsque les dialogues doivent générer d’autres boîtes de dialogue, la boîte de dialogue de premier plan doit s’exécuter en cascade vers la droite et vers le haut à partir du parent, afin qu’il soit évident pour l’utilisateur qu’il a accédé à un nouvel emplacement.

#### <a name="modality"></a>Multiples
La valeur modal signifie que les utilisateurs sont tenus d’exécuter ou d’annuler la boîte de dialogue avant de continuer. Étant donné que les boîtes de dialogue modales empêchent l’utilisateur d’interagir avec d’autres parties de l’environnement, le workflow de votre fonctionnalité doit les utiliser aussi bien que possible. Quand une opération modale est nécessaire, Visual Studio dispose d’un certain nombre de boîtes de dialogue partagées dans lesquelles vous pouvez intégrer vos fonctionnalités. Si vous devez créer une nouvelle boîte de dialogue, suivez le modèle d’interaction d’une boîte de dialogue existante avec des fonctionnalités similaires.

Lorsque les utilisateurs doivent effectuer deux activités à la fois, comme **Find** et **Replace** tout en écrivant un nouveau code, la boîte de dialogue doit être non modale afin que l’utilisateur puisse facilement basculer entre elles. Visual Studio utilise généralement des fenêtres outil pour ce type d’éditeur : tâche liée de prise en charge.

#### <a name="control-configuration"></a>Configuration du contrôle
Soyez cohérent avec les configurations de contrôle existantes qui accomplissent la même chose dans Visual Studio.

#### <a name="title-bars"></a>Barres de titre

- Le texte de la barre de titre doit refléter le nom de la commande qui l’a lancé.

- Aucune icône ne doit être utilisée dans les barres de titre de boîte de dialogue. Dans les cas où le système en requiert un, utilisez le logo Visual Studio.

- Les boîtes de dialogue ne doivent pas comporter de boutons réduire ou agrandir.

- Les boutons d’aide dans la barre de titre ont été dépréciés. Ne les ajoutez pas à de nouvelles boîtes de dialogue. Lorsqu’ils existent, ils doivent lancer une rubrique d’aide conceptuellement pertinente pour la tâche.

  ![Spécifications des indications pour les barres de titre dans les boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Spécifications des indications pour les barres de titre dans les boîtes de dialogue Visual Studio

#### <a name="control-buttons"></a>Boutons de contrôle
En général, les boutons **OK**, **Annuler** et **aide** doivent être disposés horizontalement dans le coin inférieur droit de la boîte de dialogue. L’autre pile verticale est autorisée si une boîte de dialogue contient plusieurs autres boutons au bas de la boîte de dialogue qui présentent une confusion visuelle avec les boutons de contrôle.

![Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio

La boîte de dialogue doit inclure un bouton de contrôle par défaut. Pour déterminer la meilleure commande à utiliser par défaut, choisissez parmi les options suivantes (classées par ordre de priorité) :

- Choisissez la commande la plus sûre et la plus sécurisée par défaut. Cela signifie que le choix de la commande est le plus susceptible d’empêcher la perte de données et d’éviter tout accès involontaire au système.

- Si la perte de données et la sécurité ne sont pas des facteurs, choisissez la commande par défaut en fonction de la commodité. L’inclusion de la commande la plus probable comme valeur par défaut permet d’améliorer le flux de travail de l’utilisateur lorsque le dialogue prend en charge les tâches fréquentes ou répétitives.

Évitez de choisir une action destructrice permanente pour la commande par défaut. Si une telle commande est présente, choisissez plutôt une commande plus sûre.

#### <a name="access-keys"></a>Clés d'accès
N’utilisez pas de touches d’accès pour les boutons **OK**, **Annuler** ou **aide** . Ces boutons sont mappés par défaut aux touches de raccourci :

| Nom du bouton | Raccourci clavier |
| --- | --- |
| Ok | Entrez |
| Annuler | Échap |
| Aide | F1 |

#### <a name="imagery"></a>Images
Utilisez des images avec modération dans les boîtes de dialogue. N’utilisez pas de grandes icônes dans les boîtes de dialogue simplement pour utiliser de l’espace. Utilisez des images uniquement si elles constituent une partie importante du transfert du message à l’utilisateur, comme des icônes d’avertissement ou des animations d’État.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Hiérarchisation et structuration en couches

#### <a name="prioritizing-your-ui"></a>Hiérarchisation de l’interface utilisateur
Il peut être nécessaire d’amener certains éléments de l’interface utilisateur au Forefront et de placer des options et un comportement plus avancés (y compris des commandes obscures) dans des boîtes de dialogue. Mettez les fonctionnalités couramment utilisées dans le Forefront en y faisant de la place et, en le rendant visible par défaut dans l’interface utilisateur avec une étiquette de texte lorsque la boîte de dialogue s’affiche.

#### <a name="layering-your-ui"></a>Superposition de l’interface utilisateur
Si vous avez déterminé qu’une boîte de dialogue est nécessaire, mais que les fonctionnalités associées que vous souhaitez présenter à l’utilisateur vont au-delà de ce qui peut être affiché dans une boîte de dialogue simple, vous devez définir la couche de l’interface utilisateur. Les méthodes de superposition les plus courantes utilisées par Visual Studio sont les onglets et les couloirs ou les tableaux de bord. Dans certains cas, les régions qui peuvent être développées et réduites peuvent être appropriées. L’interface utilisateur adaptative n’est généralement pas recommandée dans Visual Studio.

Il existe des avantages et des inconvénients pour les différentes méthodes de structuration de l’interface utilisateur par le biais de contrôles de type onglet. Passez en revue la liste ci-dessous pour vous assurer que vous choisissez une technique de superposition adaptée à votre situation.

##### <a name="tabbing"></a>Tabulation

| Mécanisme de commutation | Avantages et utilisation appropriée | Inconvénients et utilisation inappropriée |
| --- | --- | --- |
| Contrôle Tab | Regrouper logiquement les pages de boîtes de dialogue dans les jeux associés<br /><br />Utile pour moins de cinq (ou le nombre d’onglets qui tiennent sur une ligne dans la boîte de dialogue) pages de contrôles connexes dans la boîte de dialogue<br /><br />Les étiquettes d’onglet doivent être courtes : un ou deux mots qui peuvent facilement identifier le contenu.<br /><br />Un style de boîte de dialogue système commun<br /><br />Exemple : **&gt; Propriétés** d’un élément de l’Explorateur de fichiers | Il peut être difficile de créer des étiquettes courtes descriptives<br /><br />Ne redimensionne généralement pas les cinq derniers onglets dans une boîte de dialogue<br /><br />Inapproprié si vous disposez d’un trop grand nombre d’onglets pour une ligne (utilisez une autre technique de superposition)<br /><br />Non extensible |
| Navigation dans la barre latérale | Appareil de commutation simple qui peut accueillir plus de catégories que les onglets<br /><br />Liste plate de catégories (aucune hiérarchie)<br /><br />Extensible<br /><br />Exemple : **personnaliser... &gt; Ajouter une commande** | Il ne s’agit pas d’une bonne utilisation de l’espace horizontal s’il y a moins de trois groupes<br /><br />La tâche peut être mieux adaptée à une liste déroulante |
| Contrôle Tree | Autorise des catégories illimitées<br /><br />Permet le regroupement et/ou la hiérarchie des catégories<br /><br />Extensible<br /><br />Exemple : **&gt; Options des outils** | Des hiérarchies fortement imbriquées peuvent entraîner un défilement horizontal excessif<br /><br />Visual Studio présente un surabondance des arborescences |
| Assistant | Facilite l’achèvement des tâches en guidant l’utilisateur par le biais d’étapes séquentielles basées sur des tâches : l’Assistant représente une tâche de haut niveau et les panneaux individuels représentent les sous-tâches nécessaires pour accomplir la tâche globale.<br /><br />Utile lorsque la tâche franchit les limites de l’interface utilisateur, comme lorsque l’utilisateur aurait besoin d’utiliser plusieurs éditeurs et fenêtres outil pour terminer la tâche<br /><br />Utile lorsque la tâche nécessite une création de branche<br /><br />Utile lorsque la tâche contient des dépendances entre les étapes<br /><br />Utile lorsque plusieurs tâches similaires avec une fourche de décision peuvent être présentées dans une boîte de dialogue pour réduire le nombre de boîtes de dialogue similaires | Inapproprié pour une tâche qui n’a pas besoin d’un flux de travail séquentiel<br /><br />Les utilisateurs peuvent devenir submergés et déconcertés par un Assistant avec un trop grand nombre d’étapes<br /><br />Les assistants ont une surface d’écran limitée de manière intrinsèque |

##### <a name="hallways-or-dashboards"></a>Couloirs ou tableaux de bord
Les couloirs et les tableaux de bord sont des boîtes de dialogue ou des panneaux qui servent de points de lancement à d’autres boîtes de dialogue et fenêtres. Le « couloir » bien conçu met immédiatement en évidence uniquement les options, commandes et paramètres les plus courants, ce qui permet à l’utilisateur d’accomplir facilement des tâches courantes. À l’instar d’un couloir réaliste qui fournit des portes pour accéder aux salles sous-jacentes, l’interface utilisateur la moins courante est collectée dans des « salles » distinctes (souvent d’autres boîtes de dialogue) de fonctionnalités associées accessibles à partir du couloir principal.

Une interface utilisateur qui offre toutes les fonctionnalités disponibles dans une collection unique plutôt que la refactorisation des fonctionnalités moins courantes dans des emplacements distincts est simplement un tableau de bord.

![Concept de couloir pour l’exposition d’une interface utilisateur supplémentaire dans Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concept de couloir pour l’exposition d’une interface utilisateur supplémentaire dans Outlook

##### <a name="adaptive-ui"></a>Interface utilisateur adaptative
L’affichage ou le masquage de l’interface utilisateur en fonction de l’utilisation ou de l’expérience auto-signalée d’un utilisateur est une autre façon de présenter l’interface utilisateur nécessaire tout en masquant d’autres parties. Cela n’est pas recommandé dans Visual Studio, car les algorithmes permettant de décider quand afficher ou masquer l’interface utilisateur peuvent être délicats, et les règles sont toujours incorrectes pour un ensemble de cas.

## <a name="projects"></a><a name="BKMK_Projects"></a> Projet

### <a name="projects-in-the-solution-explorer"></a>Projets dans le Explorateur de solutions
La plupart des projets sont classés en base de référence, basé sur un répertoire ou mixte. Les trois types de projets sont pris en charge simultanément dans le Explorateur de solutions. La racine de l’expérience utilisateur dans l’utilisation des projets a lieu dans cette fenêtre. Bien que les différents nœuds de projet soient des projets de référence, de répertoire ou de type en mode mixte, il existe un modèle d’interaction commun qui doit être appliqué comme point de départ avant de se déformer en modèles utilisateur spécifiques au projet.

Les projets doivent toujours :

- Prendre en charge la possibilité d’ajouter des dossiers de projet pour organiser le contenu du projet

- Conserver un modèle cohérent pour la persistance du projet

Les projets doivent également conserver des modèles d’interaction cohérents pour :

- Supprimer des éléments de projet

- Enregistrement de documents

- Modification des propriétés d’un projet

- Modification du projet dans une autre vue

- Opérations de glisser-déplacer

### <a name="drag-and-drop-interaction-model"></a>Modèle d’interaction glisser-déplacer
Les projets sont généralement classés en tant que référence (capable de rendre persistants uniquement les références aux éléments de projet dans le stockage), basés sur un répertoire (en mesure de rendre persistants uniquement les éléments de projet stockés dans la hiérarchie d’un projet) ou mixte (en mesure de conserver les références ou les éléments physiques). L’IDE prend en charge les trois types de projets simultanément dans le **Explorateur de solutions**.

Du point de vue du glisser-déplacer, les caractéristiques suivantes doivent s’appliquer à chaque type de projet dans l' **Explorateur de solutions**:

- **Projet basé sur la référence :** Le point clé est que le projet fait glisser autour d’une référence à un élément dans le stockage. Quand un projet basé sur une référence fait office de source pour une opération de déplacement, il doit uniquement supprimer la référence à l’élément du projet. L’élément ne doit pas être réellement supprimé du disque dur. Quand un projet basé sur une référence fait office de cible pour une opération de déplacement (ou de copie), il doit ajouter une référence à l’élément source d’origine sans créer de copie privée de l’élément.

- **Projet basé sur un répertoire :** Du point de vue du glisser-déplacer, le projet glisse autour de l’élément physique plutôt qu’une référence. Lorsqu’un projet basé sur un répertoire fait office de source pour une opération de déplacement, il doit terminer la suppression de l’élément physique du disque dur, ainsi que sa suppression du projet. Lorsqu’un projet basé sur un répertoire fait office de cible pour une opération de déplacement (ou de copie), il doit faire une copie de l’élément source dans son emplacement cible.

- **Projet de cible mixte :** Du point de vue du glisser-déplacer, le comportement de ce type de projet est basé sur la nature de l’élément déplacé (soit une référence à un élément dans le stockage, soit l’élément lui-même). Le comportement correct pour les références et les éléments physiques est décrit ci-dessus.

S’il n’y avait qu’un seul type de projet dans le **Explorateur de solutions**, les opérations de glisser-déplacer seraient simples. Étant donné que chaque système de projet peut définir son propre comportement de glisser-déplacer, certaines recommandations (basées sur le comportement de glisser-déplacer de l’Explorateur Windows) doivent être suivies pour garantir une expérience utilisateur prévisible :

- Une opération glisser non modifiée dans le **Explorateur de solutions** (quand aucune touche Ctrl ou Maj n’est maintenue) doit entraîner une opération de déplacement.

- L’opération de glisser-déplacer doit également entraîner une opération de déplacement.

- L’opération CTRL-Drag doit entraîner une opération de copie.

- Les systèmes de projets mixtes et basés sur la référence prennent en charge la notion d’ajout d’un lien (ou référence) à l’élément source. Lorsque ces projets sont la cible d’une opération de glisser-déplacer (lorsque **Ctrl + Maj** est maintenu), il doit générer une référence à l’élément qui est ajouté au projet

Toutes les opérations de glisser-déplacer ne sont pas cohérentes entre les combinaisons de projets basés sur des références, basés sur des répertoires et des projets mixtes. En particulier, il est difficile de prétendre à autoriser une opération de déplacement entre un projet source basé sur un répertoire et un projet cible basé sur des références, car le projet basé sur le répertoire source doit supprimer l’élément source à l’achèvement du déplacement. Le projet basé sur la référence cible finit par se retrouver avec une référence à un élément supprimé.

Il est également trompeur de prétendre à autoriser une opération de copie entre ces types de projets, car le projet basé sur la référence cible ne doit pas créer une copie indépendante de l’élément source. De même, la combinaison de touches Ctrl + Maj vers un projet cible basé sur un répertoire ne doit pas être autorisée, car un projet basé sur un répertoire ne peut pas conserver les références. Dans les cas où l’opération de glisser-déplacer n’est pas prise en charge, l’IDE doit interdire la suppression et montrer à l’utilisateur le curseur de non-déplacement (indiqué dans le tableau du pointeur ci-dessous).

Pour implémenter correctement le comportement de glisser-déplacer, le projet source de l’opération glisser doit communiquer sa nature au projet cible. (Par exemple, est-il référence ou basé sur un répertoire ?) Ces informations sont indiquées par le format de presse-papiers qui est proposé par la source. En tant que source d’une opération de glisser-déplacer (ou de copie du presse-papiers), un projet doit proposer soit `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS` , respectivement, selon que le projet est basé sur une référence ou sur un répertoire. Ces deux formats ont le même contenu de données, qui est similaire au format Windows, `CF_HDROP` sauf que les listes de chaînes, au lieu d’être des noms de fichiers, sont une `NULL` liste de chaînes se terminant par deux `Projref` points (comme retourné par `IVsSolution::GetProjrefOfItem` ou selon le `::GetProjrefOfProject` cas).

En tant que cible d’une opération de suppression (ou de collage du presse-papiers), un projet doit accepter `CF_VSREFPROJECTITEMS` et `CF_VSSTGPROJECTITEMS` , bien que la gestion exacte de l’opération de glisser-déplacer varie en fonction de la nature du projet cible et du projet source. Le projet source déclare sa nature selon qu’il offre `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS` . La cible de la chute comprend sa propre nature et dispose donc de suffisamment d’informations pour prendre des décisions quant à la nécessité ou non d’effectuer un déplacement, une copie ou un lien. L’utilisateur modifie également l’opération de glisser-déplacer à effectuer en appuyant sur les touches Ctrl, Maj ou les touches Ctrl et Maj. Il est important que la cible de déplacement indique correctement l’opération qui sera effectuée à l’avance dans `DragEnter` ses `DragOver` méthodes et. Le **Explorateur de solutions** sait automatiquement si le projet source et le projet cible sont le même projet.

Le fait de faire glisser des éléments de projet entre des instances de Visual Studio (par exemple, d’une instance de devenv.exe à une autre) n’est pas pris en charge spécifiquement. Le **Explorateur de solutions** le désactive également directement.

L’utilisateur doit toujours être en mesure de déterminer l’effet d’une opération de glisser-déplacer en sélectionnant un élément, en le faisant glisser vers l’emplacement cible et en observant les pointeurs de souris suivants qui s’affichent avant la suppression de l’élément :

| Pointeur de souris | Commande | Description |
| :---: | --- | --- |
| ![Icône de souris « aucune suppression »](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Aucune suppression | Impossible de supprimer l’élément à l’emplacement spécifié. |
| ![Icône de souris « copier »](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copier | L’élément sera copié à l’emplacement cible. |
| ![Icône de souris « déplacer »](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Déplacer | L’élément sera déplacé vers l’emplacement cible. |
| ![Icône de souris « ajouter une référence »](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Ajouter la référence | Une référence à l’élément sélectionné sera ajoutée à l’emplacement cible. |

#### <a name="reference-based-projects"></a>Projets basés sur la référence
 Le tableau suivant résume les opérations de glisser-déplacer (et de couper/copier/coller) qui doivent être exécutées en fonction de la nature de l’élément source et des touches de modification enfoncées pour les projets cibles référencés :

| Modificateur | Category | Élément source : référence/lien | Élément source : élément physique ou système de fichiers ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacer | Lien |
| Aucun modificateur | Cible | Ajoute une référence à l’élément d’origine | Ajoute une référence à l’élément d’origine |
| Aucun modificateur | Source | Supprime la référence à l’élément d’origine | Conserve l’élément d’origine |
| Aucun modificateur | Résultats | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Maj + glisser | Action | Déplacer | Aucune suppression |
| Maj + glisser | Cible | Ajoute une référence à l’élément d’origine | Aucune suppression |
| Maj + glisser | Source | Supprime la référence à l’élément d’origine | Aucune suppression |
| Maj + glisser | Résultats | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | Aucune suppression |
| Ctrl + glisser | Action | Copier | Aucune suppression |
| Ctrl + glisser | Cible | Ajoute une référence à l’élément d’origine | Aucune suppression |
| Ctrl + glisser | Source | Conserve la référence à l’élément d’origine | Aucune suppression |
| Ctrl + glisser | Résultats | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | Aucune suppression |
| Ctrl + Maj + glisser | Action | Lien | Lien |
| Ctrl + Maj + glisser | Cible | Ajoute une référence à l’élément d’origine | Ajoute une référence à l’élément d’origine |
| Ctrl + Maj + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + Maj + glisser | Résultats | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Ctrl + Maj + glisser | Notes | Identique au comportement de glisser-déplacer pour les raccourcis dans l’Explorateur Windows. ||
| Couper/coller | Action | Déplacer | Lien |
| Couper/coller | Cible | Ajoute une référence à l’élément d’origine | Ajoute une référence à l’élément d’origine |
| Couper/coller | Source | Conserve la référence à l’élément d’origine|Conserve l’élément d’origine |
| Couper/coller | Résultats | L’élément reste à l’emplacement d’origine dans le stockage | L’élément reste à l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Lien |
| Copier/coller | Source | Ajoute une référence à l’élément d’origine | Ajoute une référence à l’élément d’origine |
| Copier/coller | Résultats | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Action | L’élément reste à l’emplacement d’origine dans le stockage | L’élément reste à l’emplacement d’origine dans le stockage |

#### <a name="directory-based-projects"></a>Projets basés sur des répertoires
Le tableau suivant résume les opérations de glisser-déplacer (et de couper/copier/coller) qui doivent être exécutées en fonction de la nature de l’élément source et des touches de modification enfoncées pour les projets cibles basés sur les répertoires :

| Modificateur | Category | Élément source : référence/lien | Élément source : élément physique ou système de fichiers ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Aucun modificateur | Action | Déplacer | Déplacer |
| Aucun modificateur | Cible | Copie l’élément dans l’emplacement cible | Copie l’élément dans l’emplacement cible |
| Aucun modificateur | Source | Supprime la référence à l’élément d’origine | Supprime la référence à l’élément d’origine |
| Maj + glisser | Action | Déplacer | Déplacer |
| Maj + glisser | Cible | Copie l’élément dans l’emplacement cible | Copie l’élément dans l’emplacement cible |
| Maj + glisser | Source | Supprime la référence à l’élément d’origine | Supprime l’élément de l’emplacement d’origine |
| Maj + glisser | Résultats | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Ctrl + glisser | Action | Copier | Copier |
| Ctrl + glisser | Cible | Copie l’élément dans l’emplacement cible | Copie l’élément dans l’emplacement cible |
| Ctrl + glisser | Source | Conserve la référence à l’élément d’origine | Conserve la référence à l’élément d’origine |
| Ctrl + glisser | Résultats | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Ctrl + Maj + glisser | | Aucune suppression | Aucune suppression |
| Couper/coller | Action | Déplacer | Déplacer |
| Couper/coller | Cible | Copie l’élément dans l’emplacement cible | Copie l’élément dans l’emplacement cible |
| Couper/coller | Source | Supprime la référence à l’élément d’origine | Supprime l’élément de l’emplacement d’origine |
| Couper/coller | Résultats | L’élément reste à l’emplacement d’origine dans le stockage | L’élément est supprimé de l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Copier |
| Copier/coller | Cible | Ajoute une référence à l’élément d’origine | Copie l’élément dans l’emplacement cible |
| Copier/coller | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Résultats | L’élément reste à l’emplacement d’origine dans le stockage | L’élément reste dans le stockage de l’emplacement d’origine |

#### <a name="mixed-target-projects"></a>Projets de cible mixte
Le tableau suivant résume les opérations de glisser-déplacer (et de couper/copier/coller) qui doivent être exécutées en fonction de la nature de l’élément source et des touches de modification enfoncées pour les projets de cible mixte :

| Modificateur | Category | Élément source : référence/lien | Élément source : élément physique ou système de fichiers ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacer | Déplacer |
| Aucun modificateur | Cible | Ajoute une référence à l’élément d’origine | Copie l’élément dans l’emplacement cible |
| Aucun modificateur | Source | Supprime la référence à l’élément d’origine | Supprime la référence à l’élément d’origine |
| Aucun modificateur | Résultats | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Maj + glisser | Action | Déplacer | Déplacer |
| Maj + glisser | Cible | Ajoute une référence à l’élément d’origine | Copie l’élément dans l’emplacement cible |
| Maj + glisser | Source | Supprime la référence à l’élément d’origine | Supprime l’élément de l’emplacement d’origine |
| Maj + glisser | Résultats | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Ctrl + glisser | Action | Copier | Copier |
| Ctrl + glisser | Cible | Ajoute une référence à l’élément d’origine | Copie l’élément dans l’emplacement cible |
| Ctrl + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + glisser | Résultats | `DROPEFFECT_ COPY` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_ COPY` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Ctrl + Maj + glisser | Action | Lien | Lien |
| Ctrl + Maj + glisser | Cible | Ajoute une référence à l’élément d’origine | Ajoute une référence à l’élément source d’origine |
| Ctrl + Maj + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + Maj + glisser | Résultats | `DROPEFFECT_ LINK` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage | `DROPEFFECT_ LINK` est retourné en tant qu’action de `::Drop` et l’élément reste à l’emplacement d’origine dans le stockage |
| Couper/coller | Action | Déplacer | Déplacer |
| Couper/coller | Cible | Copie l’élément dans l’emplacement cible | Copie l’élément dans l’emplacement cible |
| Couper/coller | Source | Supprime la référence à l’élément d’origine | Supprime l’élément de l’emplacement d’origine |
| Couper/coller | Résultats | L’élément reste à l’emplacement d’origine dans le stockage | L’élément est supprimé de l’emplacement d’origine dans le stockage |
| Copier/coller | Action | Copier | Copier |
| Copier/coller | Cible | Ajoute une référence à l’élément d’origine | Copie l’élément dans l’emplacement cible |
| Copier/coller | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller | Résultats | L’élément reste à l’emplacement d’origine dans le stockage | L’élément reste à l’emplacement d’origine dans le stockage |

Ces informations doivent être prises en considération lors de l’implémentation du glissement dans le **Explorateur de solutions**:

- Conception pour plusieurs scénarios de sélection.

- Les noms de fichiers (chemin d’accès complet) doivent être uniques dans le projet cible ou la suppression ne doit pas être autorisée.

- Les noms de dossiers doivent être uniques (sans respect de la casse) au niveau où ils sont supprimés.

- Il existe des différences de comportement entre les fichiers qui sont ouverts ou fermés au moment du glissement (non mentionné dans les scénarios ci-dessus).

- Les fichiers de niveau supérieur se comportent légèrement différemment des fichiers dans les dossiers.

Un autre problème à connaître est la façon de gérer les opérations de déplacement sur les éléments qui ont des concepteurs ou des éditeurs ouverts. Le comportement attendu est le suivant (cela s’applique à tous les types de projet) :

1. Si l’éditeur/concepteur ouvert n’a pas de modifications non enregistrées, la fenêtre Éditeur/concepteur doit être fermée en mode silencieux.

2. Si les modifications ne sont pas enregistrées dans l’éditeur/concepteur ouvert, la source de l’opération de glisser-déplacer doit attendre la suppression, puis demander à l’utilisateur d’enregistrer les modifications non validées dans les documents ouverts avant de fermer la fenêtre à l’aide d’une invite semblable à la suivante :

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Cela donne à l’utilisateur la possibilité d’enregistrer le travail en cours avant que la cible n’effectue ses copies. Une nouvelle méthode `IVsHierarchyDropDataSource2::OnBeforeDropNotify` a été ajoutée pour activer cette gestion.

La cible copie alors l’état de l’élément tel qu’il se trouve dans le stockage (sans inclure les modifications non enregistrées dans l’éditeur si l’utilisateur a choisi **non**). Une fois que la cible a terminé sa copie (dans `IVsHierarchyDropDataSource::Drop` ), la source peut terminer la partie suppression de l’opération de déplacement (dans `IVsHierarchyDropDataSource::OnDropNotify` ).

Les éditeurs avec des modifications non enregistrées doivent rester ouverts. Pour les documents contenant des modifications non enregistrées, cela signifie que la partie copie de l’opération de déplacement sera effectuée, mais que la partie supprimer sera abandonnée. Dans un scénario à sélection multiple lorsque l’utilisateur choisit **non**, les documents contenant des modifications non enregistrées ne doivent pas être fermés ou supprimés, mais ceux sans modifications non enregistrées doivent être fermés et supprimés.

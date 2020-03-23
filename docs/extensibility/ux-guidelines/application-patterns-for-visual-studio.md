---
title: Modèles d’applications pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303189"
---
# <a name="application-patterns-for-visual-studio"></a>Modèles d’application pour Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interactions de fenêtre

### <a name="overview"></a>Vue d’ensemble
Les deux principaux types de fenêtres utilisés dans Visual Studio sont les éditeurs de documents et les fenêtres d’outils. Rares, mais possibles, sont de grands dialogues sans mode. Bien que ceux-ci sont tous sans mode dans la coquille, leurs modèles sont fondamentalement différents. Cette section couvre la différence entre les fenêtres de documents, les fenêtres d’outils et les dialogues sans mode. Les modèles de dialogue modal sont couverts dans [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparaison des modèles d’utilisation des fenêtres
**Les fenêtres de documents** sont presque toujours affichées dans le document bien. Cela donne à l’éditeur de documents une « scène centrale » pour organiser des fenêtres d’outils supplémentaires autour.

Une **fenêtre d’outils** est le plus souvent affichée comme une fenêtre séparée et plus petite s’est effondrée contre le bord de l’IDE. Cela peut être visible, caché ou auto-caché. Cependant, parfois les fenêtres d’outil sont présentées dans le document bien, en décochant la **fenêtre / propriété d’amarrage** sur la fenêtre. Il en résulte plus d’immobiliers, mais aussi une décision de conception commune: lorsque vous tentez de s’intégrer dans Visual Studio, vous devez décider si votre fonctionnalité doit afficher une fenêtre d’outil ou une fenêtre de document.

**Les dialogues sans mode** sont déconseillés dans Visual Studio. La plupart des dialogues sans mode sont, par définition, des fenêtres flottantes d’outils et devraient être mis en œuvre de cette façon. Les dialogues sans mode sont autorisés dans les cas où la taille d’une fenêtre d’outil normale amarrée sur le côté de la coquille serait trop limitative. Ils sont également autorisés dans les cas où l’utilisateur serait susceptible de déplacer le dialogue à un moniteur secondaire.

Réfléchissez bien au type de conteneur dont vous avez besoin. Les considérations courantes de modèle d’utilisation pour la conception d’interface utilisateur sont dans le tableau suivant.

||Fenêtre de document|Fenêtre d’outil|Dialogue sans mode|
|-|---------------------|-----------------|---------------------|
| **Position** | Toujours bien positionné dans le document et ne s’amarre pas sur les bords de l’IDE. Il peut être "tiré" de sorte qu’il flotte séparément de la coquille principale. | Généralement tab-docked autour des bords de l’IDE, mais peut être personnalisé pour flotter, auto-caché (nonpiné), ou amarré dans le document bien.|Grande fenêtre flottante séparée de l’IDE. |
| **Modèle d’engagement** | *Engagement retardé*<br /><br /> Afin d’enregistrer les données dans un document, l’utilisateur doit émettre la commande Enregistrer le **fichier, &gt; ** **enregistrer la**commande ou **enregistrer.** Une fenêtre de document a le concept des données en elle étant "saleté" puis engagé à l’une des commandes de sauvegarde. Lors de la fermeture d’une fenêtre de document, tous les contenus sont soit enregistrés sur disque ou perdus. | *S’engager immédiatement*<br /><br /> Il n’y a pas de modèle d’enregistrement. Pour les fenêtres d’outils d’inspecteur qui aident à modifier un fichier, le fichier doit être ouvert dans l’éditeur ou le concepteur actif, et l’éditeur ou le concepteur possède l’enregistrement. | *Engagement retardé ou immédiat*<br /><br /> Le plus souvent, un grand dialogue sans mode nécessite une action pour engager des modifications et permet une opération " Annuler ", qui annule toute modification apportée au cours de la séance de dialogue.  Cela différencie un dialogue sans mode d’une fenêtre d’outil dans cette fenêtre d’outil ont toujours un modèle de validation immédiate. |
| **Visibilité** | *Ouvrir/créer (fichier) et fermer*<br /><br /> L’ouverture d’une fenêtre de document se fait soit en ouvrant un document existant, soit en utilisant un modèle pour créer un nouveau document. Il n’y \<a pas de commande « Ouvrir l’éditeur spécifique> ». | *Masquer et montrer*<br /><br /> Les fenêtres d’outils à instance unique peuvent être cachées ou affichées. Les contenus et les états dans la fenêtre de l’outil persistent, que ce soit en vue ou cachés. Les fenêtres d’outils multi-instances peuvent être fermées ainsi que cachées. Lorsqu’une fenêtre d’outil multi-instance est fermée, le contenu et l’état dans la fenêtre de l’outil sont jetés. | *Lancé à partir d’une commande*<br /><br /> Les dialogues sont lancés à partir d’une commande basée sur les tâches. |
| **Cas** | *Multi-instance*<br /><br /> Plusieurs éditeurs peuvent être ouverts en même temps et modifier différents fichiers, tandis que certains éditeurs permettent également d’ouvrir le même fichier dans plus d’un éditeur (en utilisant la commande **Window &gt; New Window).**<br /><br /> Un seul éditeur peut éditer un ou plusieurs fichiers en même temps (Project Designer). | *Une seule ou multi-instance*<br /><br /> Les contenus changent pour refléter le contexte (comme dans le navigateur de propriété) ou poussent la mise au point/le contexte vers d’autres fenêtres (Task List, Solution Explorer).<br /><br /> Les fenêtres d’outils à instance unique et multi-instance devraient être associées à la fenêtre de document active à moins qu’il n’y ait une raison impérieuse de ne pas le faire. | *Une seule instance* |
| **Exemples** | **Éditeurs de texte**, comme l’éditeur de code<br /><br /> **Concevoir des surfaces,** comme un concepteur de formulaires ou une surface de modélisation<br /><br /> **Dispositions de contrôle similaires aux dialogues,** comme le Manifest Designer | La **Solution Explorer** fournit une solution et des projets contenus dans la solution<br /><br /> Le **Server Explorer** offre une vue hiérarchique des serveurs et des connexions de données que l’utilisateur choisit d’ouvrir dans la fenêtre. L’ouverture d’un objet de la hiérarchie de la base de données, comme une requête, ouvre une fenêtre de document et permet à l’utilisateur de modifier la requête.<br /><br /> Le **navigateur de propriété** affiche les propriétés de l’objet sélectionnés soit dans une fenêtre de document ou une autre fenêtre d’outil. Les propriétés sont présentées soit dans une vue hiérarchique de grille ou dans des contrôles complexes de dialogue-like et permettent à l’utilisateur de définir les valeurs pour ces propriétés. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Fenêtres d’outils

### <a name="overview"></a>Vue d’ensemble
Les fenêtres d’outils prennent en charge le travail de l’utilisateur qui se déroule dans les fenêtres de documents. Ils peuvent être utilisés pour afficher une hiérarchie qui représente un objet racine fondamentale que Visual Studio fournit et peut manipuler.

Lors de l’examen d’une nouvelle fenêtre d’outil dans l’IDE, les auteurs doivent :

- Utilisez des fenêtres d’outils existantes adaptées aux tâches et ne créez pas de nouvelles fenêtres avec des fonctionnalités similaires. De nouvelles fenêtres d’outils ne devraient être créées que si elles offrent un « outil » ou une fonctionnalité sensiblement différent qui ne peut pas être intégré dans une fenêtre similaire, ou en transformant une fenêtre existante en un moyeu pivotant.

- Utilisez une barre de commande standard, si nécessaire, en haut de la fenêtre d’outils.

- Soyez cohérent avec les modèles déjà présents dans d’autres fenêtres d’outils pour la présentation de contrôle et la navigation du clavier.

- Soyez compatible avec la présentation de contrôle dans d’autres fenêtres d’outils.

- Rendre les fenêtres d’outils spécifiques aux documents automatiquement visibles lorsque cela est possible, de sorte qu’elles n’apparaissent que lorsque le document parent est activé.

- Assurez-vous que leur contenu de fenêtre est navigable par le clavier (touches de flèche de soutien).

#### <a name="tool-window-states"></a>États de fenêtre d’outil
Les fenêtres d’outils Visual Studio ont des états différents, dont certains sont activés par l’utilisateur (comme la fonction de cache automatique). D’autres états, comme auto-visible, permettent aux fenêtres d’outils d’apparaître dans le contexte correct et de se cacher quand il n’est pas nécessaire. Il y a cinq états de fenêtre d’outil au total.

- Des fenêtres **d’outils amarrées ou épinglées** peuvent être fixées à l’un des quatre côtés de la zone de document. L’icône pushpin apparaît dans la barre de titre de la fenêtre d’outil. La fenêtre d’outil peut être amarrée horizontalement ou verticalement le long du bord de la coque et d’autres fenêtres d’outils, et peut également être reliée à l’onglet.

- Les fenêtres **d’outils cachées** automatiques ne sont paspinned. La fenêtre peut glisser hors de la vue, laissant un onglet (avec le nom de la fenêtre de l’outil et son icône) sur le bord de la zone de document. La fenêtre de l’outil glisse lorsque l’utilisateur plane au-dessus de l’onglet.

- Les fenêtres **d’outils auto-visibles** apparaissent automatiquement lorsqu’un autre morceau d’interface utilisateur, comme un éditeur, est lancé ou se concentre.

- Les fenêtres **flottantes** de l’outil planent à l’extérieur de l’IDE. Ceci est utile pour les configurations multi-moniteurs.

- Les fenêtres **d’outils de document tabbed** peuvent être amarrées dans le document bien. Ceci est utile pour les grandes fenêtres d’outil, comme le navigateur d’objet, qui ont besoin de plus d’immobiliers que l’amarrage aux bords du cadre permet.

![États de la fenêtre Outil dans Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />États de la fenêtre Outil dans Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instance unique et multi-instance
Les fenêtres d’outils sont soit à une seule instance, soit multi-instance. Certaines fenêtres d’outils à instance unique peuvent être associées à la fenêtre de document active, tandis que les fenêtres d’outils multi-instances peuvent ne pas être. Les fenêtres d’outils multi-instances répondent à la commande **Window &gt; New Window** en créant une nouvelle instance de la fenêtre. L’image suivante illustre une fenêtre d’outil permettant la commande New Window lorsqu’une instance de la fenêtre est active :

![Fenêtre d’outil permettant la commande de « nouvelle fenêtre » lorsqu’une instance de la fenêtre est active](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Fenêtre d’outil permettant la commande de « nouvelle fenêtre » lorsqu’une instance de la fenêtre est active

Les fenêtres d’outils à instance unique peuvent être cachées ou affichées, tandis que les fenêtres d’outils multi-instances peuvent être fermées ainsi que cachées. Toutes les fenêtres d’outils peuvent être amarrées, reliées à l’onglet, flottantes ou définies sous forme de fenêtre pour enfants à interface multi-documents (MDI) (semblable à une fenêtre de document). Toutes les fenêtres d’outils doivent répondre aux commandes appropriées de gestion des fenêtres dans le menu Fenêtre :

![Commandes de gestion de fenêtre dans le menu Visual Studio Window](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Commandes de gestion de fenêtre dans le menu Visual Studio Window

#### <a name="document-specific-tool-windows"></a>Fenêtres d’outils spécifiques aux documents
Certaines fenêtres d’outils sont conçues pour changer en fonction d’un type donné de document. Ces fenêtres mettent continuellement à jour pour refléter les fonctionnalités applicables à la fenêtre de document active dans l’IDE.

Des exemples de fenêtres d’outils dont le contenu change pour refléter l’éditeur sélectionné sont la boîte à outils et le contour du document. Ces fenêtres montrent un filigrane lorsqu’un éditeur a une mise au point qui n’offre pas de contexte à la fenêtre.

#### <a name="navigable-list-tool-windows"></a>Fenêtres d’outils de liste navigables
Certaines fenêtres d’outils affichent une liste d’éléments navigables avec qui l’utilisateur peut interagir. Dans ce type de fenêtre, il devrait toujours y avoir des commentaires pour l’élément actuel dans la liste, même si la fenêtre est inactive. La liste doit répondre aux commandes **GoToNextLocation** et **GoToPrevLocation** en modifiant également l’élément actuellement sélectionné dans la fenêtre

Des exemples de fenêtres d’outils de liste navigable sont l’explorateur de solution et la fenêtre Résultats de trouver.

### <a name="tool-window-types"></a>Types de fenêtre d’outil

#### <a name="common-tool-windows-and-their-functions"></a>Fenêtres d’outils communes et leurs fonctions

**Fenêtres d’outils hiérarchiques**

| Fenêtre d’outil | Fonction |
| --- | --- |
| Explorateur de solutions | Un arbre hiérarchique qui affiche une liste de documents contenus dans des projets, des fichiers divers et des éléments de solution. L’affichage des éléments dans les projets est défini par le paquet qui possède le type de projet (par exemple, basé sur la référence, basé sur l’annuaire ou en mode mixte). |
| Affichage de classes | Un arbre hiérarchique des classes et divers éléments dans l’ensemble de travail des documents, indépendamment des dossiers eux-mêmes. |
| Explorateur de serveurs | Un arbre hiérarchique qui affiche tous les serveurs et les connexions de données dans la solution. |
| Structure du document | La structure hiérarchique du document actif. |

**Fenêtres d’outils de grille**

| Fenêtre d’outil | Fonction |
| --- | --- |
| Propriétés | Une grille qui affiche une liste de propriétés pour l’objet sélectionné, ainsi que des cueilleurs de valeur pour modifier ces propriétés. |
| Liste des tâches | Une grille qui permet à l’utilisateur de créer/modifier/supprimer des tâches et des commentaires. |

**Fenêtres d’outils de contenu**

| Fenêtre d’outil | Fonction |
| --- | --- |
| Aide | Une fenêtre qui permet aux utilisateurs d’accéder à diverses méthodes d’obtenir de l’aide, à partir de "Comment puis-je?" vidéos sur les forums MSDN. |
| Aide dynamique | Une fenêtre d’outil qui affiche des liens pour aider les sujets applicables à la sélection actuelle. |
| Explorateur d'objets | Un cadre à deux colonnes avec une liste de composants d’objets hiérarchiques dans la vitre gauche et les propriétés et méthodes de l’objet dans la colonne de droite. |

**Fenêtres d’outils de dialogue**

| Fenêtre d’outil | Fonction |
| --- | --- |
| Rechercher | Un dialogue qui permet à l’utilisateur de trouver ou de trouver et de remplacer dans divers fichiers dans la solution. |
| Recherche avancée | Un dialogue qui permet à l’utilisateur de trouver ou de trouver et de remplacer dans divers fichiers dans la solution. |

**Autres fenêtres d’outils**

::: moniker range="vs-2017"

| Fenêtre d’outil | Fonction |
| --- | --- |
| Boîte à outils | La fenêtre d’outils utilisée pour stocker les éléments qui seront déposés sur les surfaces de conception, fournissant une source de drag cohérente pour tous les concepteurs. |
| Page de démarrage | Le portail de l’utilisateur vers Visual Studio, avec accès aux flux de nouvelles des développeurs, l’aide Visual Studio, et des projets récents. Les utilisateurs peuvent également créer des pages de démarrage personnalisées en copiant le fichier\" StartPage.xaml à partir du répertoire des fichiers du programme « Common7-IDE-StartPages Visual Studio » au dossier StartPages dans le répertoire des documents Visual Studio, puis en éditant le XAML à la main, soit en l’ouvrant dans Visual Studio ou dans un autre éditeur de code. |

::: moniker-end

::: moniker range=">=vs-2019"

| Fenêtre d’outil | Fonction |
| --- | --- |
| Boîte à outils | La fenêtre d’outils utilisée pour stocker les éléments qui seront déposés sur les surfaces de conception, fournissant une source de drag cohérente pour tous les concepteurs. |

::: moniker-end

**Fenêtres d’outils Debugger**

| Fenêtre d’outil | Fonction |
| --- | --- |
| Autos ||
| Immédiat ||
| Output | La fenêtre de sortie peut être utilisée chaque fois que vous avez des événements textuels ou le statut à déclarer. |
| Mémoire ||
| Points d’arrêt ||
| Exécution en cours ||
| Documents ||
| Pile des appels ||
| Locals ||
| Montres ||
| Code Machine ||
| Registres ||
| Threads ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Conventions d’éditeur de documents

### <a name="document-interactions"></a>Interactions documentaires
Le "document bien" est le plus grand espace dans l’IDE et est l’endroit où l’utilisateur a généralement concentré leur attention afin d’accomplir leurs tâches, assisté par des fenêtres d’outils supplémentaires. Les éditeurs de documents représentent les unités fondamentales de travail que l’utilisateur ouvre et enregistre au sein de Visual Studio. Ils conservent un fort sens de la sélection lié à Solution Explorer ou à d’autres fenêtres de hiérarchie actives. L’utilisateur doit être en mesure de pointer vers l’une de ces fenêtres de hiérarchie et de savoir où le document est contenu et sa relation à la solution, le projet, ou un autre objet racine fourni par un paquet Visual Studio.

L’édition de documents nécessite une expérience utilisateur cohérente. Pour permettre à l’utilisateur de se concentrer sur la tâche à accomplir plutôt que sur la gestion des fenêtres et la recherche de commandes, sélectionnez une stratégie de vue de document qui correspond le mieux aux tâches utilisateur pour l’édition de ce type de document.

#### <a name="common-interactions-for-the-document-well"></a>Interactions communes pour le document bien

- Maintenir un modèle d’interaction cohérent dans les expériences communes **de fichier neuf** et de fichier **ouvert.**

- Mettez à jour les fonctionnalités connexes dans les fenêtres et les menus connexes lorsque la fenêtre de document s’ouvre.

- Les commandes de menu sont correctement intégrées dans des menus courants comme **Edit**, **Format**, et **Voir les** menus. Si une quantité importante de commandes spécialisées sont disponibles, alors un nouveau menu peut être créé. Ce nouveau menu ne doit être visible que lorsque le document est ciblé.

- Une barre d’outils intégrée peut être placée en haut de l’éditeur. Ceci est préférable d’avoir une barre d’outils séparée qui apparaît en dehors de l’éditeur.

- Maintenez toujours une sélection dans l’explorer de solution ou la fenêtre de hiérarchie active similaire.

- Double-cliquer sur un document dans l’explorer de solution devrait effectuer la même action que **Open**.

- Si plus d’un éditeur peut être utilisé sur un type de document, l’utilisateur doit être en mesure de remplacer ou de réinitialiser l’action par défaut sur un type de document donné à l’aide de la boîte de dialogue **Open With** en cliquant à droite sur le fichier et en sélectionnant **Open With** à partir du menu raccourci.

- Ne construisez pas un magicien dans un document bien.

### <a name="user-expectations-for-specific-document-types"></a>Attentes des utilisateurs pour des types de documents spécifiques
Il existe plusieurs types de base différents d’éditeurs de documents et chacun a un ensemble d’interactions qui sont compatibles avec d’autres du même type.

- **Éditeur textuel :** éditeur de code, fichiers journaux

- **Surface de conception:** WPF forme designer, formulaires Windows

- **Rédacteur en chef de style Dialog :** Manifest Designer, propriétés du projet

- **Concepteur de modèle :** concepteur de flux de travail, codemap, diagramme d’architecture, progression

Il existe également plusieurs types non-éditeur qui utilisent bien le document. Bien qu’ils ne modifient pas eux-mêmes les documents, ils doivent suivre les interactions standard pour les fenêtres de documents.

- **Rapports:** Rapport IntelliTrace, rapport Hyper-V, rapport de profiler

- **Tableau de bord:** Centre de diagnostic

#### <a name="text-based-editors"></a>Éditeurs textuels

- Le document participe au modèle de l’onglet d’aperçu, permettant de prévisualiser le document sans l’ouvrir.

- La structure du document peut être représentée dans une fenêtre d’outil compagnon, comme un document.

- IntelliSense (le cas échéant) se comportera de façon cohérente avec d’autres éditeurs de code.

- Les pop-ups ou l’interface utilisateur assistée suivent des styles et des modèles similaires pour l’interface utilisateur similaire existante, comme CodeLens.

- Les messages concernant l’état du document seront présentés dans un contrôle d’infobar en haut du document ou dans la barre d’état.

- L’utilisateur doit être en mesure de personnaliser l’apparence des polices et des couleurs à l’aide d’une page **Tools > Options,** soit la page Fonts et Couleurs partagées ou une page spécifique à l’éditeur.

#### <a name="design-surfaces"></a>Surfaces de conception

- Un concepteur vide devrait avoir un filigrane sur la surface indiquant comment commencer.

- Les mécanismes de commutation de vue suivront les modèles existants tels que le double clic pour ouvrir un éditeur de code, ou les onglets dans la fenêtre de document permettant l’interaction avec les deux volets.

- L’ajout d’éléments à la surface de conception doit être fait via la boîte à outils, à moins qu’une fenêtre d’outil très spécifique ne soit nécessaire.

- Les éléments de la surface suivront un modèle de sélection cohérent.

- Les barres d’outils intégrées contiennent uniquement des commandes spécifiques à des documents, et non des commandes courantes telles que **Save**.

#### <a name="dialog-style-editors"></a>Rédacteurs de style Dialog

- La disposition de contrôle devrait suivre les conventions normales de mise en page de dialogue.

- Onglets dans l’éditeur ne doit pas correspondre à l’apparence des onglets de document, ils doivent correspondre à l’un des deux styles d’onglet intérieur autorisé.

- Les utilisateurs doivent être en mesure d’interagir avec les commandes en utilisant uniquement le clavier; soit en activant l’éditeur et en tabbant à travers des contrôles, soit en utilisant des mnémoniques standard.

- Le concepteur doit utiliser le modèle Save commun. Aucun bouton d’enregistrement ou de validation global ne doit être placé sur la surface, bien que d’autres boutons puissent être appropriés.

#### <a name="model-designers"></a>Concepteurs de modèles

- Un concepteur vide devrait avoir un filigrane sur la surface indiquant comment commencer.

- L’ajout d’éléments à la surface de conception doit être fait via la boîte à outils.

- Les éléments de la surface suivront un modèle de sélection cohérent.

- Les barres d’outils intégrées contiennent uniquement des commandes spécifiques à des documents, et non des commandes courantes telles que **Save**.

- Une légende peut apparaître à la surface, soit indicative, soit un filigrane.

- L’utilisateur doit être en mesure de personnaliser l’apparence des polices/couleurs à l’aide d’une page **Tools > Options,** soit la page Fonts et Couleurs partagées ou une page spécifique à l’éditeur.

#### <a name="reports"></a>Rapports

- Les rapports sont généralement d’information seulement et ne participent pas au modèle Save. Cependant, ils peuvent inclure des interactions telles que des liens vers d’autres informations pertinentes ou des sections qui s’étendent et s’effondrent.

- La plupart des commandes sur la surface doivent être des hyperliens, pas des boutons.

- La mise en page doit inclure un en-tête et suivre les lignes directrices standard de mise en page du rapport.

#### <a name="dashboards"></a>Tableaux de bord

- Les tableaux de bord n’ont pas eux-mêmes un modèle d’interaction, mais servent de moyen d’offrir une variété d’autres outils.

- Ils ne participent pas au modèle Save.

- Les utilisateurs doivent être en mesure d’interagir avec les contrôles en utilisant uniquement le clavier, soit en activant l’éditeur et en tabbing à travers les contrôles ou en utilisant des mnémoniques standard.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Dialogues

### <a name="introduction"></a>Introduction
Les dialogues dans Visual Studio doivent généralement prendre en charge une unité discrète du travail de l’utilisateur, puis être rejetés.

Si vous avez déterminé que vous avez besoin d’un dialogue, vous avez trois choix, par ordre de préférence :

1. Intégrez vos fonctionnalités dans l’un des dialogues partagés dans Visual Studio.

2. Créez votre propre dialogue à l’aide d’un modèle trouvé dans un dialogue similaire existant.

3. Créez un nouveau dialogue, suivant les lignes directrices sur l’interaction et la mise en page.

Cette section décrit comment choisir le modèle de dialogue correct dans les flux de travail Visual Studio et les conventions communes pour la conception de dialogue.

### <a name="themes"></a>Thèmes
Les dialogues en visual studio suivent l’un des deux styles de base :

#### <a name="standard-unthemed"></a>Standard (non jugé)
La majorité des dialogues sont des dialogues d’utilité standard et devraient être inexcusées. Ne pas re-template des contrôles communs ou tenter de créer des boutons ou des contrôles "modernes" stylisés. Les contrôles et l’apparence chromée suivent les [directives standard d’interaction Windows Desktop pour les boîtes de dialogue](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Thème
Les dialogues de « signature » de spécialité peuvent être thématiques. Les dialogues thématiques ont un aspect distinct, qui a également quelques modèles spéciaux d’interaction associés au modèle. Thème de votre dialogue que s’il répond à ces exigences :

- Le dialogue est une expérience commune qui sera vu et utilisé souvent ou par de nombreux utilisateurs (par exemple, le dialogue **du nouveau projet.**

- Le dialogue contient des éléments importants de la marque de produits (par exemple, le dialogue **sur les paramètres de compte).**

- Le dialogue fait partie intégrante d’un flux plus large qui comprend d’autres dialogues thématiques (par exemple, le dialogue **Add Connected Service).**

- Le dialogue est un élément important d’une expérience qui joue un rôle stratégique dans la promotion ou la différenciation d’une version produit.

Lors de la création d’un dialogue thématique, utilisez les couleurs de l’environnement appropriées et suivez les modèles de mise en page et d’interaction corrects. (Voir [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Conception de dialogue
Les dialogues bien conçus tiennent compte des éléments suivants :

- La tâche utilisateur prise en charge

- Le style de texte de dialogue, la langue et la terminologie

- Choix de contrôle et conventions d’assurance-chômage

- Spécifications de mise en page visuelle et alignement de contrôle

- Accès par le clavier

#### <a name="content-organization"></a>Organisation du contenu
Considérez les différences entre ces types de dialogues de base :

- [Les dialogues simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) présentent des contrôles dans une seule fenêtre modale. La présentation peut inclure des variantes de modèles de contrôle complexes, y compris un cueilleur de champ ou une barre d’icône.

- [Les dialogues superposés](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) sont utilisés pour tirer le meilleur parti de l’écran immobilier quand un seul morceau d’interface utilisateur comprend plusieurs groupes de contrôles. Les regroupements du dialogue sont « superposés » par le biais de commandes d’onglets, de contrôles de liste de navigation ou de boutons afin que l’utilisateur puisse choisir le groupement à voir à un moment donné.

- Les assistants sont [utiles](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) pour diriger l’utilisateur à travers une séquence logique d’étapes vers l’achèvement d’une tâche. Une série de choix sont offerts en panneaux séquentiels, introduisant parfois différents flux de travail (« branches ») dépendant d’un choix fait dans le panneau précédent.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Des dialogues simples
Un simple dialogue est une présentation des contrôles dans une seule fenêtre modale. Cette présentation peut inclure des variations de modèles de contrôle complexes, comme un cueilleur de champ. Pour les dialogues simples, suivez la disposition générale standard ainsi que toute mise en page spécifique requise pour les groupes de contrôle complexes.

![>Create Strong Name Key est un exemple de dialogue simple dans Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Create Strong Name Key est un exemple de dialogue simple dans Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Dialogues superposés
Les dialogues superposés comprennent des onglets, des tableaux de bord et des arbres encastrés. Ils sont utilisés pour maximiser les immobiliers quand il ya plusieurs groupes de contrôles offerts dans un seul morceau de l’interface utilisateur. Les regroupements sont superposés afin que l’utilisateur puisse choisir le groupement à voir à tout moment.

Dans le cas le plus simple, le mécanisme de commutation entre les groupes est un contrôle de l’onglet. Plusieurs alternatives sont disponibles. Voir Prioriser et superposer pour savoir comment choisir le style le plus approprié.

Le dialogue **Tools &gt; Options** est un exemple de dialogue en couches à l’aide d’un arbre encastré :

![Tools > Options est un exemple de dialogue en couches dans Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Tools > Options est un exemple de dialogue en couches dans Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Assistants
Les assistants sont utiles pour diriger l’utilisateur à travers une séquence logique d’étapes dans l’accomplissement d’une tâche. Une série de choix sont offerts dans les panneaux séquentiels, et l’utilisateur doit continuer à travers chaque étape avant de passer à l’autre. Une fois que des défauts suffisants sont disponibles, le bouton **Finition** est activé.

 Les assistants modaux sont utilisés pour des tâches qui :

- Contenir la branchement, où différents chemins sont offerts en fonction des choix des utilisateurs

- Contenir les dépendances entre les étapes, lorsque les étapes suivantes dépendent de l’entrée de l’utilisateur de l’étape précédente(s)

- Sont suffisamment complexes pour que l’interface utilisateur soit utilisée pour expliquer les choix offerts et les résultats possibles à chaque étape.

- Sont transactionnels, nécessitant un ensemble d’étapes à remplir dans son intégralité avant tout changement sont engagés

### <a name="common-conventions"></a>Conventions communes
Pour obtenir une conception et une fonctionnalité optimales avec vos dialogues, suivez ces conventions sur la taille du dialogue, la position, les normes, la configuration de contrôle et l’alignement, le texte de l’interface utilisateur, les barres de titre, les boutons de contrôle et les touches d’accès.

Pour des lignes directrices spécifiques à la mise en page, voir [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Size
Les dialogues doivent s’adapter dans une résolution minimale de l’écran 1024x768, et la taille initiale du dialogue ne doit pas dépasser 900x700 pixels. Les dialogues peuvent être résizables, mais ce n’est pas une exigence.

Il y a deux recommandations pour les dialogues resizables :

1. Qu’une taille minimale est une définition pour le dialogue qui permettra d’optimiser pour l’ensemble de contrôle sans coupure, et de s’ajuster pour tenir compte de la croissance de localisation raisonnable.

2. Que la taille à l’échelle de l’utilisateur persiste d’une session à l’autre. Par exemple, si l’utilisateur balance un dialogue à 150 %, alors un lancement ultérieur du dialogue s’affichera à 150 %.

#### <a name="position"></a>Position
Les dialogues doivent apparaître centrés dans l’IDE lors du premier lancement. La dernière position des dialogues non résizables n’a pas besoin d’être persistée, de sorte qu’ils apparaîtront centrés sur les lancements ultérieurs.

Pour les dialogues résizables, la taille doit être persistée lors des lancements ultérieurs. Pour les dialogues modaux résizables, la position n’a pas besoin d’être persistée. Les afficher centrés dans l’IDE empêche la possibilité que le dialogue apparaisse dans une position imprévisible ou inutilisable lorsque la configuration d’affichage de l’utilisateur a changé.

Pour les dialogues sans mode qui peuvent être repositionnés, la position de l’utilisateur doit être maintenue sur les lancements ultérieurs, car le dialogue peut être utilisé fréquemment comme une partie intégrante d’un flux de travail plus important.

Lorsque les dialogues doivent engendrer d’autres dialogues, le dialogue le plus élevé doit cascader vers la droite et vers le bas à partir du parent de sorte qu’il est évident pour l’utilisateur qu’ils ont navigué vers un nouvel endroit.

#### <a name="modality"></a>Modalité
Etre modal signifie que les utilisateurs sont tenus de remplir ou d’annuler le dialogue avant de continuer. Étant donné que les dialogues modaux empêchent l’utilisateur d’interagir avec d’autres parties de l’environnement, le flux de tâches de votre fonctionnalité devrait les utiliser avec le plus d’unie possible. Lorsqu’une opération modale est nécessaire, Visual Studio dispose d’un certain nombre de dialogues partagés dans qui vous pouvez intégrer vos fonctionnalités. Si vous devez créer un nouveau dialogue, suivez le modèle d’interaction d’un dialogue existant avec des fonctionnalités similaires.

Lorsque les utilisateurs ont besoin d’effectuer deux activités à la fois, comme **Trouver** et **remplacer** lors de l’écriture de nouveau code, le dialogue doit être sans mode afin que l’utilisateur peut facilement basculer entre eux. Visual Studio utilise généralement des fenêtres d’outils pour ce genre de tâche liée à l’éditeur.

#### <a name="control-configuration"></a>Configuration de contrôle
Soyez cohérent avec les configurations de contrôle existantes qui accomplissent la même chose dans Visual Studio.

#### <a name="title-bars"></a>Barres de titre

- Le texte de la barre de titre doit refléter le nom de la commande qui l’a lancé.

- Aucune icône ne doit être utilisée dans les barres de titre de dialogue. Dans les cas où le système en nécessite un, utilisez le logo Visual Studio.

- Les dialogues ne devraient pas avoir de minimiser ou maximiser les boutons.

- Les boutons d’aide dans la barre de titre ont été dépréciés. Ne les ajoutez pas à de nouveaux dialogues. Lorsqu’ils existent, ils devraient lancer un sujet d’aide qui est conceptuellement pertinent à la tâche.

  ![Spécifications de ligne directrice pour les barres de titre dans les dialogues Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Spécifications de ligne directrice pour les barres de titre dans les dialogues Visual Studio

#### <a name="control-buttons"></a>Boutons de contrôle
En général, **OK**, **Annuler**, et **boutons d’aide** doivent être disposés horizontalement dans le coin inférieur droit du dialogue. La pile verticale alternative est autorisée si un dialogue a plusieurs autres boutons au bas du dialogue qui présenterait une confusion visuelle avec les boutons de commande.

![Configurations acceptables pour les boutons de contrôle dans les dialogues Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurations acceptables pour les boutons de contrôle dans les dialogues Visual Studio

Le dialogue doit inclure un bouton de contrôle par défaut. Pour déterminer la meilleure commande à utiliser comme par défaut, choisissez parmi les options suivantes (énumérées par ordre de priorité) :

- Choisissez la commande la plus sûre et la plus sécurisée comme par défaut. Cela signifie choisir la commande la plus susceptible d’éviter la perte de données et d’éviter l’accès involontaire au système.

- Si la perte de données et la sécurité ne sont pas des facteurs, choisissez la commande par défaut en fonction de la commodité. L’inclusion de la commande la plus probable que la valeur par défaut permettra d’améliorer le flux de travail de l’utilisateur lorsque le dialogue prend en charge des tâches fréquentes ou répétitives.

Évitez de choisir une action destructrice permanente pour la commande par défaut. Si une telle commande est présente, choisissez une commande plus sûre comme par défaut à la place.

#### <a name="access-keys"></a>Clés d'accès
N’utilisez pas de clés d’accès pour **OK,** **Annuler,** ou **aider** les boutons. Ces boutons sont cartographiés en touches raccourcies par défaut :

| Nom du bouton | Raccourci clavier |
| --- | --- |
| OK | Entrez |
| Annuler | Échap |
| Aide | F1 |

#### <a name="imagery"></a>Imagerie
Utilisez des images avec parcimonie dans les dialogues. N’utilisez pas de grandes icônes dans les dialogues simplement pour utiliser l’espace. Utilisez des images uniquement si elles sont une partie importante de transmettre le message à l’utilisateur, comme des icônes d’avertissement ou des animations de statut.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Priorisation et superposition

#### <a name="prioritizing-your-ui"></a>Prioriser votre assurance-chômage
Il pourrait être nécessaire d’mettre certains éléments d’interface utilisateur à l’avant-garde et de placer un comportement et des options plus avancés (y compris des commandes obscures) dans les dialogues. Apportez la fonctionnalité couramment utilisée à l’avant-plan en faisant de la place pour elle, et en la rendant visible par défaut dans l’interface utilisateur avec une étiquette de texte lorsque le dialogue est affiché.

#### <a name="layering-your-ui"></a>Superposition de votre interface utilisateur
Si vous avez déterminé qu’un dialogue est nécessaire, mais la fonctionnalité connexe que vous souhaitez présenter à l’utilisateur va au-delà de ce qui peut être affiché dans un dialogue simple, alors vous devez superposer votre interface utilisateur. Les méthodes de superposition les plus courantes utilisées par Visual Studio sont les onglets et les couloirs ou les tableaux de bord. Dans certains cas, les régions qui peuvent s’étendre et s’effondrer pourraient être appropriées. L’interface utilisateur adaptative n’est généralement pas recommandée dans Visual Studio.

Il y a des avantages et des inconvénients à différentes méthodes de superposition de l’interface utilisateur par des contrôles de type onglet. Examinez la liste ci-dessous pour vous assurer que vous choisissez une technique de superposition qui convient à votre situation.

##### <a name="tabbing"></a>Tabulation

| Mécanisme de commutation | Avantages et utilisation appropriée | Inconvénients et utilisation inappropriée |
| --- | --- | --- |
| Contrôle Tab | Logiquement des pages de dialogue de groupe dans les ensembles connexes<br /><br />Utile pour moins de cinq (ou le nombre d’onglets qui s’intègrent dans une rangée à travers le dialogue) pages de contrôles connexes dans le dialogue<br /><br />Les étiquettes d’onglet doivent être courtes : un ou deux mots qui peuvent facilement identifier le contenu<br /><br />Un système commun de dialogue style<br /><br />Exemple : **Propriétés d’objets d’explorateur &gt; de fichiers** | Il peut être difficile de faire des étiquettes courtes descriptives<br /><br />Généralement ne pas l’échelle passé cinq onglets dans un dialogue<br /><br />Inapproprié si vous avez trop d’onglets pour une rangée (utiliser une technique de superposition alternative)<br /><br />Pas extensible |
| Navigation sidebar | Dispositif de commutation simple qui peut accueillir plus de catégories que d’onglets<br /><br />Liste plate des catégories (pas de hiérarchie)<br /><br />extensibilité ;<br /><br />Exemple : **Personnalisez... Ajouter &gt; commande** | Pas une bonne utilisation de l’espace horizontal s’il y a moins de trois groupes<br /><br />La tâche pourrait être mieux adaptée à un abandon |
| Contrôle Tree | Permet des catégories illimitées<br /><br />Permet le regroupement et/ou la hiérarchie des catégories<br /><br />extensibilité ;<br /><br />Exemple : **Options d’outils &gt; ** | Les hiérarchies fortement imbriquées peuvent causer un défilement horizontal excessif<br /><br />Visual Studio a une surabondance de vues sur les arbres |
| Assistant | Aide à l’accomplissement des tâches en guidant l’utilisateur à travers des étapes séquentielles basées sur les tâches : l’assistant représente une tâche de haut niveau et les panneaux individuels représentent des sous-bandes nécessaires pour accomplir la tâche globale<br /><br />Utile lorsque la tâche franchit les limites d’Ui, comme lorsque l’utilisateur aurait autrement à utiliser plusieurs éditeurs et fenêtres d’outils pour accomplir la tâche<br /><br />Utile lorsque la tâche nécessite une branchement<br /><br />Utile lorsque la tâche contient des dépendances entre les étapes<br /><br />Utile lorsque plusieurs tâches similaires avec une fourchette de décision peuvent être présentées dans un dialogue pour réduire le nombre de dialogues similaires différents | Inapproprié pour toute tâche qui ne nécessite pas un flux de travail séquentiel<br /><br />Les utilisateurs peuvent devenir submergés et confus par un magicien avec trop d’étapes<br /><br />Les assistants ont intrinsèquement limité l’immobilier d’écran |

##### <a name="hallways-or-dashboards"></a>Couloirs ou tableaux de bord
Les couloirs et les tableaux de bord sont des dialogues ou des panneaux qui servent de points de lancement à d’autres dialogues et fenêtres. Le « couloir » bien conçu ne fait immédiatement surface que les options, les commandes et les paramètres les plus courants, ce qui permet à l’utilisateur d’accomplir facilement des tâches courantes. Comme un couloir du monde réel fournit des portes pour accéder aux chambres derrière eux, ici l’interface utilisateur moins commune est recueillie dans des «chambres» séparées (souvent d’autres dialogues) de fonctionnalités connexes qui peuvent être consultés à partir du couloir principal.

Alternativement, une interface utilisateur qui offre toutes les fonctionnalités disponibles dans une seule collection plutôt que de refactoriser la fonctionnalité moins commune dans des emplacements distincts est simplement un tableau de bord.

![Concept de couloir pour exposer l’interface utilisateur supplémentaire dans Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concept de couloir pour exposer l’interface utilisateur supplémentaire dans Outlook

##### <a name="adaptive-ui"></a>Interface utilisateur adaptative
Afficher ou cacher l’interface utilisateur en fonction de l’utilisation ou de l’expérience auto-déclarée d’un utilisateur est une autre façon de présenter l’interface utilisateur nécessaire tout en cachant d’autres portions. Ceci n’est pas recommandé dans Visual Studio, car les algorithmes pour décider quand afficher ou cacher l’interface utilisateur peut être difficile, et les règles seront toujours mauvaises pour certains ensemble de cas.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projets

### <a name="projects-in-the-solution-explorer"></a>Projets dans l’explorateur de solution
La plupart des projets sont classés comme basés sur des références, basés sur des annuaires ou mixtes. Les trois types de projets sont pris en charge simultanément dans le Solution Explorer. La racine de l’expérience utilisateur dans le travail avec des projets a lieu à l’intérieur de cette fenêtre. Bien que différents nœuds de projet soient des projets de référence, d’annuaire ou de type mode mixte, il existe un modèle d’interaction commun qui devrait être appliqué comme point de départ avant de diverger dans les modèles d’utilisateurs spécifiques au projet.

Les projets doivent toujours :

- Soutenir la possibilité d’ajouter des dossiers de projet pour organiser le contenu du projet

- Maintenir un modèle cohérent pour la persistance du projet

Les projets devraient également maintenir des modèles d’interaction cohérents pour :

- Suppression des éléments du projet

- Enregistrement des documents

- Montage de propriété de projet

- Modifier le projet dans une autre vue

- Opérations de drag-and-drop

### <a name="drag-and-drop-interaction-model"></a>Modèle d’interaction Drag-and-drop
Les projets se classent généralement comme des références basées sur des références (capables de ne persister que des références aux éléments de projet en stockage), à base d’annuaire (capable de ne persister que des éléments de projet stockés physiquement dans la hiérarchie d’un projet) ou mixtes (capables de persister les références ou des objets physiques). L’IDE accueille simultanément les trois types de projets au sein de la **Solution Explorer**.

Du point de vue de la traînée et de la baisse, les caractéristiques suivantes devraient s’appliquer à chaque type de projet au sein de la **Solution Explorer**:

- **Projet fondé sur des références :** Le point clé est que le projet traîne autour d’une référence à un élément en stockage. Lorsqu’un projet fondé sur des références agit comme source d’opération de déménagement, il ne doit supprimer que la référence à l’élément du projet. L’élément ne doit pas réellement être supprimé du disque dur. Lorsqu’un projet fondé sur des références sert de cible pour une opération de déménagement (ou de copie), il doit ajouter une référence à l’élément source d’origine sans faire une copie privée de l’élément.

- **Projet d’annuaire :** D’un point de vue de drag-and-drop, le projet traîne autour de l’élément physique plutôt que d’une référence. Lorsqu’un projet d’annuaire agit comme source d’opération de déménagement, il doit finir par supprimer l’élément physique du disque dur et le retirer du projet. Lorsqu’un projet d’annuaire agit comme une cible pour une opération de déménagement (ou de copie), il doit faire une copie de l’élément source à son emplacement cible.

- **Projet à objectif mixte :** D’un point de vue de drag-and-drop, le comportement de ce type de projet est basé sur la nature de l’élément traîné (soit une référence à un élément en stockage ou l’élément lui-même). Le comportement correct pour les références et les éléments physiques sont décrits ci-dessus.

S’il n’y avait qu’un seul type de projet dans le **Solution Explorer,** alors les opérations de drag-and-drop seraient simples. Étant donné que chaque système de projet a la capacité de définir son propre comportement de drag-and-drop, certaines lignes directrices (basées sur le comportement de drag-and-drop de Windows Explorer) doivent être suivies pour assurer une expérience utilisateur prévisible :

- Une opération de traînée non modifiée dans le **Solution Explorer** (lorsque ni les clés Ctrl ni Shift ne sont retenues) devraient entraîner une opération de déménagement.

- L’opération de la traînée de vitesse devrait également entraîner une opération de déplacement.

- L’opération Ctrl-drag devrait entraîner une opération de copie.

- Les systèmes de projets mixtes et basés sur des références soutiennent la notion d’ajout d’un lien (ou d’une référence) à l’élément source. Lorsque ces projets sont la cible d’une opération de drag-and-drop (lorsque **Ctrl et Shift** sont retenus), il devrait se traduire par une référence à l’élément ajouté au projet

Toutes les opérations de drag-and-drop ne sont pas raisonnables entre les combinaisons de projets axés sur les références, basés sur les annuaires et mixtes. En particulier, il est problématique de prétendre permettre un déménagement entre un projet de source d’annuaire et un projet cible basé sur la référence parce que le projet basé sur l’annuaire source devra supprimer l’élément source une fois le déménagement terminé. Le projet basé sur la référence cible se retrouverait alors avec une référence à un élément supprimé.

Il est également trompeur de prétendre permettre une opération de copie entre ces types de projets parce que le projet ciblé fondé sur la référence ne devrait pas faire une copie indépendante de l’élément source. De même, le dragage de Ctrl et Shift vers un projet cible basé sur l’annuaire ne devrait pas être autorisé parce qu’un projet axé sur l’annuaire n’est pas en mesure de maintenir des références. Dans les cas où l’opération de drag-and-drop n’est pas prise en charge, l’IDE doit interdire la goutte et montrer à l’utilisateur le curseur sans goutte (indiqué dans le tableau de pointage ci-dessous).

Pour mettre en œuvre correctement le comportement de drag-and-drop, le projet source de la traînée doit communiquer sa nature au projet cible. (Par exemple, est-il basé sur la référence ou l’annuaire?) Ces informations sont indiquées par le format de presse-papiers qui est offert par la source. En tant que source d’une opération de drag `CF_VSREFPROJECTITEMS` (ou de copie de presse-papiers), un projet devrait offrir, soit ou `CF_VSSTGPROJECTITEMS` respectivement, selon que le projet est basé sur la référence ou sur l’annuaire. Ces deux formats ont le même contenu de `CF_HDROP` données, qui est similaire au format Windows, sauf que`NULL` les `Projref` listes de chaînes, `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` au lieu d’être des noms de fichiers, sont une liste à double fin de chaînes (au retour ou le cas échéant).

Comme la cible d’une baisse (ou d’une `CF_VSREFPROJECTITEMS` opération `CF_VSSTGPROJECTITEMS`de pâte de presse), un projet doit accepter les deux et, bien que la manipulation exacte de l’opération de drag-and-drop varie en fonction de la nature du projet cible et du projet source. Le projet source déclare sa nature `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`par qu’il offre ou . La cible de la baisse comprend sa propre nature et dispose ainsi de suffisamment d’informations pour prendre des décisions quant à savoir si un déménagement, une copie ou un lien doit être effectué. L’utilisateur modifie également le fonctionnement de la traînée et de la chute qui doit être effectué en appuyant sur les touches Ctrl, Shift ou les deux Ctrl et Shift. Il est important que la cible de largage indique `DragEnter` correctement `DragOver` quelle opération sera effectuée à l’avance dans ses méthodes et méthodes. **L’Explorer Solution** sait automatiquement si le projet source et le projet cible sont le même projet.

Le fait de glisser des éléments de projet dans des instances de Visual Studio (par exemple, d’un exemple de devenv.exe à un autre) n’est spécifiquement pas pris en charge. La **Solution Explorer** désactive également directement cela.

L’utilisateur doit toujours être en mesure de déterminer l’effet d’une opération de drag-and-drop en sélectionnant un élément, en le faisant glisser à l’emplacement cible, et en observant lequel des pointeurs de souris suivants apparaît avant que l’élément est abandonné:

| Pointeur de souris | Commande | Description |
| :---: | --- | --- |
| ![Icône de souris « aucune suppression »](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Pas de baisse | L’article ne peut pas être déposé à l’emplacement spécifié. |
| ![Icône de souris « copier »](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copier | L’élément sera copié à l’emplacement cible. |
| ![Icône de souris « déplacer »](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Déplacer | L’article sera déplacé à l’emplacement cible. |
| ![Icône de souris « ajouter une référence »](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Ajouter la référence | Une référence à l’élément sélectionné sera ajoutée à l’emplacement cible. |

#### <a name="reference-based-projects"></a>Projets fondés sur des références
 Le tableau suivant résume les opérations de drag-and-drop (ainsi que les opérations de coupe/copie/coller) qui doivent être effectuées en fonction de la nature de l’élément source et des clés modificateurs pressées pour les projets cibles référencés :

| Modificateur | Category | Élément source : Référence/Lien | Élément source : Élément physique`CF_HDROP`ou système de fichier ( ) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacer | Lien |
| Aucun modificateur | Cible | Ajoute la référence à l’élément original | Ajoute la référence à l’élément original |
| Aucun modificateur | Source | Supprime la référence à l’élément original | Conserve l’article original |
| Aucun modificateur | Résultats | `DROPEFFECT_MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_LINK`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Shift-Drag | Action | Déplacer | Pas de baisse |
| Shift-Drag | Cible | Ajoute la référence à l’élément original | Pas de baisse |
| Shift-Drag | Source | Supprime la référence à l’élément original | Pas de baisse |
| Shift-Drag | Résultats | `DROPEFFECT_MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | Pas de baisse |
| Ctrl-Drag | Action | Copier | Pas de baisse |
| Ctrl-Drag | Cible | Ajoute la référence à l’élément original | Pas de baisse |
| Ctrl-Drag | Source | Conserve la référence à l’élément original | Pas de baisse |
| Ctrl-Drag | Résultats | `DROPEFFECT_COPY`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | Pas de baisse |
| Ctrl-Shift-Drag | Action | Lien | Lien |
| Ctrl-Shift-Drag | Cible | Ajoute la référence à l’élément original | Ajoute la référence à l’élément original |
| Ctrl-Shift-Drag | Source | Conserve la référence à l’élément original | Conserve l’article original |
| Ctrl-Shift-Drag | Résultats | `DROPEFFECT_LINK`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_LINK`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Ctrl-Shift-Drag | Remarque | Tout comme le comportement de drag-and-drop pour les raccourcis dans Windows Explorer. ||
| Coupe/Pâte | Action | Déplacer | Lien |
| Coupe/Pâte | Cible | Ajoute la référence à l’élément original | Ajoute la référence à l’élément original |
| Coupe/Pâte | Source | Conserve la référence à l’élément original|Conserve l’article original |
| Coupe/Pâte | Résultats | L’article reste à l’emplacement d’origine dans le stockage | L’article reste à l’emplacement d’origine dans le stockage |
| Copie/Pâte | Action | Copier | Lien |
| Copie/Pâte | Source | Ajoute la référence à l’élément original | Ajoute la référence à l’élément original |
| Copie/Pâte | Résultats | Conserve la référence à l’élément original | Conserve l’article original |
| Copie/Pâte | Action | L’article reste à l’emplacement d’origine dans le stockage | L’article reste à l’emplacement d’origine dans le stockage |

#### <a name="directory-based-projects"></a>Projets d’annuaire
Le tableau suivant résume les opérations de drag-and-drop (ainsi que les opérations de coupe/copie/coller) qui doivent être effectuées en fonction de la nature de l’élément source et des clés modificateurs pressées pour les projets cibles basés sur l’annuaire :

| Modificateur | Category | Élément source : Référence/Lien | Élément source : Élément physique`CF_HDROP`ou système de fichier ( ) |
|-----------------|----------| - | - |
| Aucun modificateur | Action | Déplacer | Déplacer |
| Aucun modificateur | Cible | Copies de l’élément à l’emplacement cible | Copies de l’élément à l’emplacement cible |
| Aucun modificateur | Source | Supprime la référence à l’élément original | Supprime la référence à l’élément original |
| Shift-Drag | Action | Déplacer | Déplacer |
| Shift-Drag | Cible | Copies de l’élément à l’emplacement cible | Copies de l’élément à l’emplacement cible |
| Shift-Drag | Source | Supprime la référence à l’élément original | Supprime l’élément de l’emplacement d’origine |
| Shift-Drag | Résultats | `DROPEFFECT_MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Ctrl-Drag | Action | Copier | Copier |
| Ctrl-Drag | Cible | Copies de l’élément à l’emplacement cible | Copies de l’élément à l’emplacement cible |
| Ctrl-Drag | Source | Conserve la référence à l’élément original | Conserve la référence à l’élément original |
| Ctrl-Drag | Résultats | `DROPEFFECT_COPY`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_COPY`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Ctrl-Shift-Drag | | Pas de baisse | Pas de baisse |
| Coupe/Pâte | Action | Déplacer | Déplacer |
| Coupe/Pâte | Cible | Copies de l’élément à l’emplacement cible | Copies de l’élément à l’emplacement cible |
| Coupe/Pâte | Source | Supprime la référence à l’élément original | Supprime l’élément de l’emplacement d’origine |
| Coupe/Pâte | Résultats | L’article reste à l’emplacement d’origine dans le stockage | L’article est supprimé de l’emplacement d’origine dans le stockage |
| Copie/Pâte | Action | Copier | Copier |
| Copie/Pâte | Cible | Ajoute la référence à l’élément original | Copies de l’élément à l’emplacement cible |
| Copie/Pâte | Source | Conserve l’article original | Conserve l’article original |
| Copie/Pâte | Résultats | L’article reste à l’emplacement d’origine dans le stockage | L’article reste dans l’emplacement original dans le stockage |

#### <a name="mixed-target-projects"></a>Projets à cibles mixtes
Le tableau suivant résume les opérations de drag-and-drop (ainsi que les opérations de coupe/copie/coller) qui doivent être effectuées en fonction de la nature de l’élément source et des clés modificateurs pressées pour les projets à cible mixte :

| Modificateur | Category | Élément source : Référence/Lien | Élément source : Élément physique`CF_HDROP`ou système de fichier ( ) |
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacer | Déplacer |
| Aucun modificateur | Cible | Ajoute la référence à l’élément original | Copies de l’élément à l’emplacement cible |
| Aucun modificateur | Source | Supprime la référence à l’élément original | Supprime la référence à l’élément original |
| Aucun modificateur | Résultats | `DROPEFFECT_ MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_ MOVE`est retourné comme `::Drop` action et l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Shift-Drag | Action | Déplacer | Déplacer |
| Shift-Drag | Cible | Ajoute la référence à l’élément original | Copies de l’élément à l’emplacement cible |
| Shift-Drag | Source | Supprime la référence à l’élément original | Supprime l’élément de l’emplacement d’origine |
| Shift-Drag | Résultats | `DROPEFFECT_ MOVE`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_ MOVE`est retourné comme `::Drop` action et l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Ctrl-Drag | Action | Copier | Copier |
| Ctrl-Drag | Cible | Ajoute la référence à l’élément original | Copies de l’élément à l’emplacement cible |
| Ctrl-Drag | Source | Conserve la référence à l’élément original | Conserve l’article original |
| Ctrl-Drag | Résultats | `DROPEFFECT_ COPY`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_ COPY`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Ctrl-Shift-Drag | Action | Lien | Lien |
| Ctrl-Shift-Drag | Cible | Ajoute la référence à l’élément original | Ajoute la référence à l’élément source d’origine |
| Ctrl-Shift-Drag | Source | Conserve la référence à l’élément original | Conserve l’article original |
| Ctrl-Shift-Drag | Résultats | `DROPEFFECT_ LINK`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage | `DROPEFFECT_ LINK`est retourné comme `::Drop` action et l’article reste dans l’emplacement original dans le stockage |
| Coupe/Pâte | Action | Déplacer | Déplacer |
| Coupe/Pâte | Cible | Copies de l’élément à l’emplacement cible | Copies de l’élément à l’emplacement cible |
| Coupe/Pâte | Source | Supprime la référence à l’élément original | Supprime l’élément de l’emplacement d’origine |
| Coupe/Pâte | Résultats | L’article reste à l’emplacement d’origine dans le stockage | L’article est supprimé de l’emplacement d’origine dans le stockage |
| Copie/Pâte | Action | Copier | Copier |
| Copie/Pâte | Cible | Ajoute la référence à l’élément original | Copies de l’élément à l’emplacement cible |
| Copie/Pâte | Source | Conserve l’article original | Conserve l’article original |
| Copie/Pâte | Résultats | L’article reste à l’emplacement d’origine dans le stockage | L’article reste à l’emplacement d’origine dans le stockage |

Ces détails doivent être pris en considération lors de la mise en œuvre de dragage dans **l’Explorer Solution**:

- Conception pour plusieurs scénarios de sélection.

- Les noms de fichiers (chemin complet) doivent être uniques dans l’ensemble du projet cible ou la baisse ne doit pas être autorisée.

- Les noms de dossier doivent être uniques (insensibles aux cas) au niveau où ils sont supprimés.

- Il existe des différences de comportement entre les fichiers qui sont ouverts ou fermés au moment de la traînée (non mentionné dans les scénarios ci-dessus).

- Les fichiers de haut niveau se comportent légèrement différemment des fichiers dans les dossiers.

Une autre question à connaître est de savoir comment gérer les opérations de déménagement sur les éléments qui ont des concepteurs ou des éditeurs ouverts. Le comportement attendu est le suivant (cela s’applique à tous les types de projets):

1. Si l’éditeur/concepteur ouvert n’a pas de changements nonavés, alors la fenêtre de l’éditeur/concepteur doit être silencieusement fermée.

2. Si l’éditeur/concepteur ouvert a des modifications nonavées, alors la source de la traînée doit attendre que la goutte se produise, puis demander à l’utilisateur d’enregistrer les modifications non engagées dans les documents ouverts avant de fermer la fenêtre avec une invite similaire à ce qui suit:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Cela donne à l’utilisateur la possibilité d’enregistrer le travail en cours avant que la cible ne fasse ses copies. Une nouvelle `IVsHierarchyDropDataSource2::OnBeforeDropNotify` méthode a été ajoutée pour permettre cette manipulation.

La cible copiera ensuite l’état de l’élément tel qu’il est en stockage (sans compter les modifications nonavées dans l’éditeur si **l’utilisateur**a choisi No ). Une fois que la cible `IVsHierarchyDropDataSource::Drop`a terminé sa copie (en), la source a `IVsHierarchyDropDataSource::OnDropNotify`la possibilité de compléter la partie de suppression de l’opération de déménagement (en ).

Tous les éditeurs avec des modifications nonavées doivent être laissés ouverts. Pour les documents avec des modifications nonavées, cela signifie que la partie de copie de l’opération de déménagement sera effectuée, mais la partie de suppression sera avortée. Dans un scénario de sélection multiple lorsque **l’utilisateur**choisit Non , les documents avec des modifications nonavées ne doivent pas être fermés ou supprimés, mais ceux qui n’ont pas de modifications nonavées doivent être fermés et supprimés.
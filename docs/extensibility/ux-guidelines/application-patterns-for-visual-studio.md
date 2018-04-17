---
title: Modèles d’application pour Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a793651660c456213c0e91c0d6c6474cccf3f7d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="application-patterns-for-visual-studio"></a>Modèles d’application pour Visual Studio
##  <a name="BKMK_WindowInteractions"></a> Interactions de la fenêtre  
  
### <a name="overview"></a>Vue d'ensemble  
Les deux types de fenêtre principale utilisées dans Visual Studio sont des fenêtres Outil et les éditeurs de document. Rare mais possible, est des boîtes de dialogue non modales volumineux. Bien que ce sont toutes non modales dans l’interpréteur de commandes, leurs schémas sont fondamentalement différentes. Cette section aborde la différence entre les fenêtres de document, les fenêtres Outil et boîtes de dialogue non modales. Modèles de boîte de dialogue modale sont traités dans [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparaison des modèles d’utilisation de la fenêtre  
**Fenêtres de document** sont presque toujours affichés dans le document correctement. Ainsi, l’éditeur de document une « phase center » pour organiser les fenêtres Outil supplémentaires.  
  
A **fenêtre outil** s’affichent généralement comme une fenêtre distincte, le plus petite réduite sur le bord de l’IDE. Cela peut être visible, caché ou masquées automatiquement. Toutefois, parfois, les fenêtres Outil sont présentés dans le document bien, en désactivant le **/ l’ancrage de la fenêtre** propriété dans la fenêtre. Cela entraîne plus immobilier, mais également la décision de conception commune : lorsque vous tentez d’intégrer à Visual Studio, vous devez décider si votre fonction doit afficher une fenêtre outil ou une fenêtre de document.  
  
**Les boîtes de dialogue non modales** est déconseillé dans Visual Studio. Les boîtes de dialogue plus non modales sont, par définition, les fenêtres Outil flottantes et doivent être implémentées de cette façon. Les boîtes de dialogue non modales sont autorisées dans les cas où la taille d’une fenêtre outil normal ancrée sur le côté de l’interpréteur de commandes est trop limitée. Ils sont également autorisées dans les cas où l’utilisateur serait susceptible de déplacer la boîte de dialogue à un moniteur secondaire.  
  
Envisagez avec précaution sur le type conteneur. Common considérations sur le modèle d’utilisation pour la conception de l’interface utilisateur sont dans le tableau suivant.  
  
||Fenêtre de document|Fenêtre outil|Boîte de dialogue non modal|  
|-|---------------------|-----------------|---------------------|  
| **Position** | Toujours placé dans le document et ne pas ancrer des bords de l’IDE. Il peut être » retiré » afin qu’il flotte séparément à partir de l’interpréteur de commandes principal. | Généralement ancrés autour des bords de l’IDE, mais peut être personnalisé de flottement, masquées automatiquement (unpinned), ou ancré également dans le document.|Grande fenêtre flottante distinct à partir de l’IDE. |  
| **Valider le modèle** | *Validation différée*<br /><br /> Pour enregistrer les données dans un document, l’utilisateur doit émettre le **fichier &gt; enregistrer**, **enregistrer en tant que**, ou **Enregistrer tout** commande. Une fenêtre de document a le concept des données qu’il contient « modifications », puis validé à un de l’entité commandes. Lors de la fermeture d’une fenêtre de document, tout le contenu est enregistré sur le disque soit perdu. | *Validation immédiate*<br /><br /> Il n’existe aucun enregistrement modèle. Pour les fenêtres d’outil inspecteur qui aident à la modification d’un fichier, le fichier doit être ouvert dans l’éditeur ou concepteur actif, et l’éditeur ou le Concepteur de propriétaire de l’enregistrement. | *Validation ultérieure ou immédiate*<br /><br /> Le plus souvent, une grande boîte de dialogue non modale requiert une action de validation des modifications et permet une opération « Cancel », ce qui annule les modifications apportées dans la session de la boîte de dialogue.  Celle-ci distingue une boîte de dialogue non modale à partir d’une fenêtre outil dans la mesure où les fenêtres Outil ont toujours un modèle de validation immédiate. |  
| **Visibilité** | *Ouverture/de création (fichier) et fermer*<br /><br /> Ouverture d’une fenêtre de document est effectuée à l’ouverture d’un document existant ou à l’aide d’un modèle pour créer un nouveau document. Il existe aucune « ouvrir \<spécifique de l’éditeur > » commande. | *Masquer et afficher*<br /><br /> Windows de l’outil à instance unique peuvent être masqués ou affichés. Contenu et les États dans la fenêtre outil persistent si dans la vue ou masqué. Les fenêtres Outil à instances multiples peuvent être fermés ainsi que masqués. Lorsqu’une fenêtre d’outil à instances multiples est fermée, le contenu et l’état dans la fenêtre outil est ignoré. | *Lancé à partir d’une commande*<br /><br /> Les boîtes de dialogue sont lancées à partir d’une commande de tâche. |  
| **Instances** | *Instances multiples*<br /><br /> Plusieurs éditeurs peuvent être ouvertes en même temps et modification de fichiers différent, alors que certains éditeurs permettent également le même fichier ouvert dans plusieurs éditeurs (à l’aide de la **fenêtre &gt; nouvelle fenêtre** commande).<br /><br /> Un éditeur unique peut modifier un ou plusieurs fichiers en même temps (Concepteur de projet). | *Instance unique ou multiniveau*<br /><br /> Contenu change pour refléter le contexte (comme dans l’Explorateur de propriétés) ou de type push de focus/contexte d’autres fenêtres (liste des tâches, l’Explorateur de solutions).<br /><br /> Les fenêtres Outil à instance unique et plusieurs instances doivent être associés à la fenêtre de document actif sauf s’il existe une bonne raison de pas à. | *Instance unique* |  
| **Exemples** | **Éditeurs de texte**, telles que l’éditeur de code<br /><br /> **Les aires de conception**, comme un concepteur de formulaires ou une surface de modélisation<br /><br /> **Contrôler les mises en page semblables aux boîtes de dialogue**, telles que le Concepteur de manifeste | Le **l’Explorateur de solutions** fournit une solution et les projets contenus dans la solution<br /><br /> Le **l’Explorateur de serveurs** fournit une vue hiérarchique des connexions de serveurs et des données que l’utilisateur choisit d’ouvrir dans la fenêtre. Ouverture d’un objet de la hiérarchie de la base de données, comme une requête, ouvre une fenêtre de document et permet à l’utilisateur de modifier la requête.<br /><br /> Le **Explorateur de propriétés** affiche les propriétés de l’objet sélectionné dans une fenêtre de document ou une autre fenêtre outil. Les propriétés sont présentées dans une vue hiérarchique de grille ou dans les contrôles de boîtes de dialogue complexes et autoriser l’utilisateur à définir les valeurs de ces propriétés. | |  
  
##  <a name="BKMK_ToolWindows"></a> Fenêtres Outil  
  
### <a name="overview"></a>Vue d'ensemble  
Fenêtres Outil prennent en charge de travail de l’utilisateur qui se produit dans les fenêtres de document. Ils peuvent être utilisés pour présenter une hiérarchie qui représente un objet racine fondamentaux que Visual Studio fournit et peut manipuler.  
  
Lorsque vous envisagez une fenêtre outil dans l’IDE, les auteurs doivent :  
  
-   Utilisez des fenêtres Outil existantes approprié à la tâche et pas créer d’autres ayant des fonctionnalités similaires. Nouvelles fenêtres Outil doivent être créés uniquement si elles offrent un « tool » sensiblement différente ou une fonctionnalité qui ne peut pas être intégrée dans une fenêtre similaire, ou en activant une fenêtre existante à un concentrateur de croisement dynamique.  
  
-   Utilisez une barre de commandes standard, si nécessaire, en haut de la fenêtre outil.  
  
-   Être compatibles avec les modèles déjà présentes dans les autres fenêtres d’outils pour la navigation de clavier et de présentation du contrôle.  
  
-   Être cohérent avec la présentation du contrôle dans d’autres fenêtres Outil.  
  
-   Rendre les fenêtres Outil de document spécifique visibles automatiquement lorsque cela est possible, afin qu’ils apparaissent uniquement lorsque le document parent est activé.  
  
-   Vérifiez que leur contenu de la fenêtre est navigable par le clavier (touches de direction de prise en charge).  
  
#### <a name="tool-window-states"></a>États de la fenêtre outil  
Fenêtres Outil Visual Studio ont des états différents, dont certains sont activés par utilisateur (par exemple, la fonctionnalité Masquer automatiquement). Autres États, comme visibles automatiquement, autoriser les fenêtres Outil apparaisse dans le contexte approprié et masquer lors ne pas nécessaire. Il existe cinq États de la fenêtre outil au total.  
  
-   **Ancré/épinglé** fenêtres Outil peuvent être attachés à un des quatre côtés de la zone de document. L’icône de punaise apparaît dans la barre de titre de fenêtre outil. La fenêtre outil peut être ancrée horizontalement ou verticalement le long du bord de l’interpréteur de commandes et d’autres fenêtres d’outils et peut également être la liée par onglets.  
  
-   **Masquée automatiquement** fenêtres Outil sont libérés. La fenêtre peut glisser en dehors de la vue, en laissant un onglet (avec le nom de la fenêtre outil et son icône) sur le bord de la zone de document. La fenêtre outil coulisse lorsqu’un utilisateur pointe sur l’onglet.  
  
-   **Visibles automatiquement** fenêtres Outil s’affichent automatiquement lorsqu’une autre partie de l’interface utilisateur, comme un éditeur, qui est lancée ou obtention du focus.  
  
-   **Flottante** fenêtres Outil placez le curseur en dehors de l’IDE. Cela est utile pour les configurations à plusieurs écrans.  
  
-   **Document à onglets** fenêtres Outil peuvent être ancrées dans le document bien. Cela est utile pour les fenêtres d’outil volumineux, tels que l’Explorateur d’objets, qui a besoin de davantage de place que permet d’ancrage pour les bords du cadre.  
  
![Outil d’états de la fenêtre dans Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />États de la fenêtre Outil dans Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Instance unique et à plusieurs instances  
Fenêtres Outil sont à instance unique ou à plusieurs instances. Certaines fenêtres Outil à instance unique peuvent être associées à la fenêtre de document actif, tandis que les fenêtres d’outil à instances multiples ne peuvent pas. Les fenêtres Outil multi-instance répondent à la **fenêtre &gt; nouvelle fenêtre** commande en créant une nouvelle instance de la fenêtre. L’image suivante illustre une fenêtre outil de l’activation de la commande nouvelle fenêtre lorsqu’une instance de la fenêtre est active :  
  
![Fenêtre outil activant la commande « Nouvelle fenêtre » lorsqu’une instance de la fenêtre est active](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Fenêtre outil activant la commande « Nouvelle fenêtre » lorsqu’une instance de la fenêtre est active  
  
Windows de l’outil à instance unique peuvent être masqués ou affichés, alors que les fenêtres d’outil à instances multiples peuvent être fermés ainsi que masqués. Toutes les fenêtres Outil peuvent être ancrées, liée par onglets, flottante ou défini comme une fenêtre d’enfant d’Interface multidocument (MDI) (semblable à une fenêtre de document). Toutes les fenêtres Outil doivent répondre aux commandes de gestion de fenêtre appropriée dans le menu Fenêtre :  
  
![Commandes de gestion de fenêtre dans le menu de la fenêtre Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Commandes de gestion de fenêtre dans le menu de la fenêtre Visual Studio
  
#### <a name="document-specific-tool-windows"></a>Fenêtres de document spécifique  
Certaines fenêtres Outil sont conçus pour modifier selon un type de document donné. Ces fenêtres continuellement mise à jour pour refléter les fonctionnalités sont applicables à la fenêtre de document actif dans l’IDE.  
  
La boîte à outils et la structure du Document en sont des exemples de fenêtres Outil dont le contenu sont modifiés pour refléter l’éditeur sélectionné. Ces fenêtres montrent un filigrane lorsqu’un éditeur a le focus qui n’offre pas de contexte à la fenêtre.  
  
#### <a name="navigable-list-tool-windows"></a>Fenêtres liste  
Certaines fenêtres Outil affichent une liste d’éléments navigables, avec que l’utilisateur peut interagir. Dans ce type de fenêtre, il doit toujours y avoir des commentaires pour l’élément actuel dans la liste, même si la fenêtre est inactive. La liste doit répondre à la **GoToNextLocation** et **GoToPrevLocation** commandes par change également l’élément actuellement sélectionné dans la fenêtre  
  
Fenêtres d’outils de liste sont l’Explorateur de solutions et de la fenêtre Résultats de la recherche.  
  
### <a name="tool-window-types"></a>Types de fenêtres Outil  
  
#### <a name="common-tool-windows-and-their-functions"></a>Les fenêtres Outil courants et leurs fonctions

**Fenêtres Outil hiérarchique**
| Fenêtre outil | Fonction | 
| --- | --- | 
| Explorateur de solutions | Une arborescence hiérarchique qui affiche une liste des documents contenus dans les projets, les fichiers divers et les éléments de solution. L’affichage des éléments dans des projets est défini par le package qui possède le type de projet (par exemple, les types référence basée, basée sur Active ou en mode mixte). | 
| Affichage de classes | Arborescence hiérarchique des classes et des divers éléments dans la plage de travail de documents, indépendamment des fichiers eux-mêmes. | 
| Explorateur de serveurs | Une arborescence hiérarchique qui affiche toutes les connexions de serveurs et des données de la solution. | 
| Structure du document | La structure hiérarchique du document actif. | 

**Fenêtres Outil de grille**
| Fenêtre outil | Fonction | 
| --- | --- | 
| Propriétés | Une grille qui affiche une liste de propriétés de l’objet sélectionné, ainsi que les sélecteurs de valeur pour modifier ces propriétés. | 
| Liste des tâches | Une grille qui lui permet de créer/modifier/supprimer des tâches et des commentaires. | 

**Fenêtres Outil contenu**
| Fenêtre outil | Fonction | 
| --- | --- | 
| Help | Une fenêtre qui permet aux utilisateurs l’accès à différentes méthodes de l’obtention d’aide, à partir de « Comment faire ? » vidéos sur les forums MSDN. | 
| Aide dynamique | Une fenêtre outil qui affiche des liens vers des rubriques applicables à la sélection actuelle d’aide. | 
| Explorateur d'objets | Un jeu de cadres de deux colonnes avec une liste de composants hiérarchique d’objets dans le volet gauche de l’objet propriétés et méthodes dans la colonne de droite. | 

**Fenêtres Outil de boîte de dialogue**
| Fenêtre outil | Fonction | 
| --- | --- | 
| Find | Une boîte de dialogue qui permet à l’utilisateur à rechercher ou rechercher et remplacer dans les fichiers divers dans la solution. |
| Recherche avancée | Une boîte de dialogue qui permet à l’utilisateur à rechercher ou rechercher et remplacer dans les fichiers divers dans la solution. | 

**Autres fenêtres d’outils**
| Fenêtre outil | Fonction | 
| --- | --- | 
| Boîte à outils | La fenêtre outil est utilisée pour stocker les éléments qui sont supprimés sur les surfaces de conception, en fournissant une source de glissement cohérente pour tous les concepteurs. |
| Page de démarrage | Portail de l’utilisateur pour Visual Studio, avec un accès aux flux d’informations pour les développeurs, l’aide de Visual Studio et projets récents. Utilisateurs peuvent également créer des pages de démarrage personnalisées en copiant le fichier StartPage.xaml à partir de la « Common7\IDE\StartPages\" répertoire des fichiers de programme Visual Studio dans le dossier StartPages dans Visual Studio documents active, puis soit en modifiant le code XAML à la main ou ouvrez-le dans Visual Studio ou un autre éditeur de code. | 

**Fenêtres du débogueur**
| Fenêtre outil | Fonction | 
| --- | --- |
| Autos ||  
| Immédiat ||  
| Sortie | La fenêtre sortie peut être utilisée chaque fois que vous avez des événements textuelles ou des États pour déclarer. |  
| Mémoire ||  
| Points d’arrêt ||  
| En cours d'exécution ||  
| Documents ||  
| Pile des appels ||  
| Variables locales ||  
| Observations ||  
| Code Machine ||  
| Registres ||  
| Threads ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a> Conventions de l’éditeur de document  
  
### <a name="document-interactions"></a>Interactions de document  
« Barre d’outils document » est le plus grand espace dans l’IDE et où l’utilisateur généralement se sont concentrées leur attention afin de terminer leurs tâches, assistés par les fenêtres Outil supplémentaires. Les éditeurs de document représentent les unités fondamentales de travail que l’utilisateur s’ouvre et l’enregistre dans Visual Studio. Ils conservent une forte de sélection liée l’Explorateur de solutions ou d’autres fenêtres de la hiérarchie active. L’utilisateur doit être en mesure de pointer vers l’un de ces fenêtres de hiérarchie et de savoir où le document est contenu et sa relation à la solution, le projet ou un autre objet racine fourni par un package Visual Studio.  
  
Modification de documents nécessite une expérience utilisateur cohérente. Pour autoriser l’utilisateur à se concentrer sur la tâche en cours et non sur la gestion des fenêtres et les commandes de recherche, sélectionnez une stratégie d’affichage de document qui répond le mieux aux tâches utilisateur pour la modification de ce type de document.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interactions communes pour le bien de document  
  
-   Mettre à jour un modèle d’interaction cohérent dans le common **nouveau fichier** et **ouvrir le fichier** rencontre.  
  
-   Mettre à jour des fonctionnalités associées dans les menus et les fenêtres associées lors de la fenêtre de document s’ouvre.  
  
-   Commandes de menu sont correctement intégrées dans les menus courants, tels que **modifier**, **Format**, et **vue** menus. Si une quantité substantielle de commandes spécialisées est disponible, un nouveau menu peut être créé. Ce nouveau menu doit être visible uniquement lorsque le document a le focus.  
  
-   Une barre d’outils incorporée peut être placé en haut de l’éditeur. Cela est préférable d’avoir une barre d’outils qui apparaît en dehors de l’éditeur.  
  
-   Toujours conserver une sélection dans l’Explorateur de solutions ou d’un actif similaire fenêtre de la hiérarchie.  
  
-   Double-clic sur un document dans l’Explorateur de solutions doit effectuer la même action que **ouvrir**.  
  
-   Si plus d’un éditeur peut être utilisé sur un type de document, l’utilisateur doit être en mesure de remplacer ou de réinitialiser l’action par défaut sur un type de document donné à l’aide de la **ouvrir avec** boîte de dialogue en cliquant sur le fichier et en sélectionnant **ouvert Avec** dans le menu contextuel.  
  
-   Ne créez pas également un Assistant dans un document.  
  
### <a name="user-expectations-for-specific-document-types"></a>Attentes des utilisateurs pour les types de document spécifique  
Il existe plusieurs types de base différents éditeurs de document et chacun possède un ensemble d’interactions sont cohérents avec d’autres utilisateurs du même type.  
  
-   **Éditeur de texte :** éditeur de code, des fichiers journaux  
  
-   **Aire de conception :** concepteur, Windows forms WPF forms  
  
-   **Éditeur de style de la boîte de dialogue :** Concepteur de manifeste, propriétés du projet  
  
-   **Générateur de modèles :** le Concepteur de flux de travail, codemap, diagramme d’architecture, progression  
  
Il existe également plusieurs types non éditeur qui utilisent le document correctement. Pendant qu’ils ne modifiez pas les documents eux-mêmes, ils n’avez pas besoin de suivre des interactions standard pour les fenêtres de document.  
  
-   **Rapports :** IntelliTrace de rapports, rapports de Hyper-V, le rapport de profileur  
  
-   **Tableau de bord :** Hub de diagnostic  
  
#### <a name="text-based-editors"></a>Éditeurs de texte  
  
-   Le document participe au modèle onglet Aperçu pour afficher un aperçu du document sans l’ouvrir.  
  
-   La structure du document peut être représentée dans une fenêtre d’outil d’accompagnement, comme une structure du document.  
  
-   IntelliSense (le cas échéant) se comportent de manière cohérente avec les autres éditeurs de code.  
  
-   Les fenêtres contextuelles ou l’interface utilisateur d’assistance suivez des styles et modèles similaires pour interface utilisateur similaires existante, tels que CodeLens.  
  
-   Messages d’état du document seront affiche dans un contrôle de barre d’informations en haut du document ou dans la barre d’état.  
  
-   L’utilisateur doit être en mesure de personnaliser l’apparence des polices et couleurs à l’aide un **Outils > Options** page, la page polices et couleurs partagée ou un spécifiques à l’éditeur.  
  
#### <a name="design-surfaces"></a>Surfaces de dessin  
  
-   Un concepteur vide doit avoir un filigrane sur la surface de la prise en main.  
  
-   Mécanismes de basculement entre les vues suit les modèles existants tels que double-cliquez pour ouvrir un éditeur de code ou des onglets dans la fenêtre de document permettant l’interaction avec les deux volets.  
  
-   Ajout d’éléments à l’aire de conception doit être effectuée via la boîte à outils, sauf si une fenêtre outil très spécifique est requise.  
  
-   Éléments sur l’aire suit un modèle de sélection cohérente.  
  
-   Barres d’outils incorporées contiennent des commandes d’uniquement, pas courantes des commandes spécifiques du document comme **enregistrer**.  
  
#### <a name="dialog-style-editors"></a>Éditeurs de style de la boîte de dialogue  
  
-   La disposition des contrôles doit suivre les conventions de mise en page de boîte de dialogue normale.  
  
-   Onglets de l’éditeur ne doivent pas correspondre à l’apparence des onglets de document, ils doivent correspondre à un des deux styles onglet intérieurs autorisées.  
  
-   Les utilisateurs doivent être en mesure d’interagir avec les contrôles à l’aide du clavier uniquement. soit par activation de l’éditeur et la tabulation entre les contrôles ou à l’aide de mnémoniques standards.  
  
-   Le concepteur doit utiliser le common enregistrer le modèle. Aucun enregistrement global ou un bouton de validation ne doit être placé sur la surface, bien que les autres boutons peut s’avérer nécessaire.  
  
#### <a name="model-designers"></a>Concepteurs de modèles  
  
-   Un concepteur vide doit avoir un filigrane sur la surface de la prise en main.  
  
-   Ajout d’éléments à l’aire de conception doit être effectuée via la boîte à outils.  
  
-   Éléments sur l’aire suit un modèle de sélection cohérente.  
  
-   Barres d’outils incorporées contiennent des commandes d’uniquement, pas courantes des commandes spécifiques du document comme **enregistrer**.  
  
-   Une légende peut apparaître sur la surface, indicative ou filigrane.  
  
-   L’utilisateur doit être en mesure de personnaliser l’apparence des polices/couleurs à l’aide un **Outils > Options** page, la page polices et couleurs partagée ou un spécifiques à l’éditeur.  
  
#### <a name="reports"></a>Rapports  
  
-   Les rapports sont généralement des informations uniquement et ne font pas partie du modèle d’enregistrement. Toutefois, elles peuvent inclure des interactions telles que des liens vers d’autres informations pertinentes ou des sections développer et réduire.  
  
-   La plupart des commandes sur l’aire de doivent être des liens hypertexte, pas de boutons.  
  
-   Mise en page doit inclure un en-tête et suivez les instructions de mise en page de rapport standard.  
  
#### <a name="dashboards"></a>Tableaux de bord  
  
-   Tableaux de bord n’avait un modèle d’interaction eux-mêmes, mais servir un moyen pour offrir une variété d’autres outils.  
  
-   Elles n’interviennent pas dans le modèle de sauvegarde.  
  
-   Les utilisateurs doivent être en mesure d’interagir avec les contrôles à l’aide du clavier uniquement, en activant l’éditeur et de tabulation des contrôles ou à l’aide de mnémoniques standards.  
  
##  <a name="BKMK_Dialogs"></a> Boîtes de dialogue  
  
### <a name="introduction"></a>Introduction  
Les boîtes de dialogue dans Visual Studio doivent généralement prendre en charge d’une petite unité de travail de l’utilisateur et puis être sera ignorés.  
  
Si vous avez déterminé que vous avez besoin d’une boîte de dialogue, vous avez trois possibilités, par ordre de préférence :  
  
1.  Intégrer des fonctionnalités dans une des boîtes de dialogue partagées dans Visual Studio.  
  
2.  Créer votre propre boîte de dialogue à l’aide d’un modèle trouvé dans une boîte de dialogue similaire existant.  
  
3.  Créer une nouvelle boîte de dialogue, interaction suivant et les instructions de mise en page.  
  
Cette section décrit comment choisir le modèle de boîte de dialogue correct dans le flux de travail de Visual Studio et des conventions pour la conception de la boîte de dialogue communes.  
  
### <a name="themes"></a>Thèmes  
Les boîtes de dialogue dans Visual Studio suivent l’une des deux styles de base :  
  
#### <a name="standard-unthemed"></a>Standard (unthemed)  
La plupart des boîtes de dialogue sont les boîtes de dialogue utilitaire standard et doit être unthemed. Effectuez pas les contrôles communs remodéliser ou essayez de créer des boutons « modernes » stylisés ou des contrôles. Contrôles et l’apparence de chrome suivez [directives d’interaction de bureau Windows standards pour les boîtes de dialogue](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>À thème  
Les boîtes de dialogue spécialité « signature » peuvent être à thème. Les boîtes de dialogue à thème ont une apparence distincte, qui possède également des modèles d’interaction spéciale associées au style. Thème votre boîte de dialogue uniquement si elle répond aux exigences suivantes :  
  
-   La boîte de dialogue est une expérience commune qui est visible et utilisée par de nombreux utilisateurs ou souvent (par exemple, le **nouveau projet** boîte de dialogue.  
  
-   La boîte de dialogue contient les éléments de marque de produit qu’ils le veuillent (par exemple, le **les paramètres de compte** boîte de dialogue).  
  
-   La boîte de dialogue s’affiche en tant que partie intégrante d’un flux de plus grande qui inclut d’autres boîtes de dialogue à thème (par exemple, le **ajouter un Service connecté** boîte de dialogue).  
  
-   La boîte de dialogue est importante pour une expérience qui joue un rôle stratégique de promotion ou différencier une version de produit.  
  
Lorsque vous créez une boîte de dialogue à thème, utiliser les couleurs de l’environnement approprié et suivez la disposition correcte et les modèles d’interaction. (Consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Conception de la boîte de dialogue  
Les boîtes de dialogue bien conçues tenir sur les éléments suivants :  
  
-   La tâche de l’utilisateur qui est pris en charge  
  
-   Le style de texte de boîte de dialogue, la langue et la terminologie  
  
-   Choix de contrôle et les conventions de l’interface utilisateur  
  
-   Alignement de spécification et le contrôle de disposition visuelle  
  
-   Accès par le clavier  
  
#### <a name="content-organization"></a>Organisation du contenu  
Prendre en compte les différences entre ces types de base de boîtes de dialogue :  
  
-   [Les boîtes de dialogue simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) présentent des contrôles dans une seule fenêtre modale. La présentation peut inclure les variantes des modèles de contrôle complexe, y compris un sélecteur de champ ou une barre d’icônes.  
  
-   [Couches de boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) permettent de tirer parti de l’espace d’écran lorsqu’un élément unique de l’interface utilisateur comporte plusieurs groupes de contrôles. Les regroupements de la boîte de dialogue sont « en couche » via les contrôles d’onglet, les contrôles de liste de navigation ou des boutons afin que l’utilisateur peut choisir le regroupement pour voir à un moment donné.  
  
-   [Assistants](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sont utiles pour diriger l’utilisateur via une séquence logique d’étapes vers la fin d’une tâche. Une série de choix sont proposées dans les panneaux séquentiel, parfois présentation différents flux de travail (« branches ») dépend d’un choix dans le panneau de configuration précédente.  
  
####  <a name="BKMK_SimpleDialogs"></a> Boîtes de dialogue simples  
Une boîte de dialogue simple est une présentation des contrôles dans une seule fenêtre modale. Cette présentation peut inclure les variantes des modèles de contrôle complexe, par exemple un sélecteur de champ. Pour les boîtes de dialogue simples, suivez la disposition générale standard, ainsi que toute mise en page spécifique requises pour les regroupements de contrôle complexe.
  
![> créer une clé de nom fort est un exemple de boîte de dialogue simple dans Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Créer une clé de nom fort est un exemple de boîte de dialogue simple dans Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a> Boîtes de dialogue en couche  
Les boîtes de dialogue superposées incluent les onglets, les tableaux de bord et les arbres incorporés. Ils sont utilisés pour optimiser immobilier lorsqu’il existe plusieurs groupes de contrôles proposés dans un seul élément de l’interface utilisateur. Les regroupements sont superposées afin que l’utilisateur peut choisir le regroupement pour afficher à tout moment.  
  
Dans le cas le plus simple, le mécanisme de basculer entre les regroupements est un contrôle onglet. Il existe plusieurs alternatives. Consultez la définition de la priorité et la superposition pour savoir comment choisir le style plus approprié.  
  
Le **outils &gt; Options** boîte de dialogue est un exemple de boîte de dialogue en couches à l’aide d’une arborescence incorporée :  
  
![Outils > Options est un exemple d’une boîte de dialogue superposée dans Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Outils > Options est un exemple d’une boîte de dialogue superposée dans Visual Studio.
  
####  <a name="BKMK_Wizards"></a> Assistants  
Assistants sont utiles pour diriger l’utilisateur via une séquence logique d’étapes dans la réalisation d’une tâche. Une série de choix sont proposés dans les panneaux séquentielles, et l’utilisateur doit continuer à chaque étape avant de passer à la suivante. Une fois que les valeurs par défaut suffisantes sont disponibles, le **Terminer** bouton est activé.  
  
 Assistants modales sont utilisés pour les tâches qui :  
  
-   Contient la création de branches, où les différents chemins d’accès sont proposées en fonction du choix de l’utilisateur  
  
-   Contient des dépendances entre les étapes, où les étapes suivantes dépendent des entrées utilisateur à partir de l’ou les étapes précédente  
  
-   Sont suffisamment complexe que l’interface utilisateur doit servir pour expliquer les choix proposés et les résultats possibles dans chaque étape.  
  
-   Sont transactionnelles, nécessitant un ensemble d’étapes à effectuer dans son intégralité avant que les modifications soient validées  
  
### <a name="common-conventions"></a>Conventions courantes  
Pour obtenir une conception optimale et les fonctionnalités avec vos boîtes de dialogue, suivez ces conventions sur la taille de la boîte de dialogue, position, normes, configuration du contrôle et l’alignement, l’interface utilisateur texte, les barres de titre, les boutons de commande et les clés d’accès.  
  
Pour connaître les instructions spécifiques à la disposition, consultez [disposition pour Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Size  
Les boîtes de dialogue doivent tenir dans une résolution d’écran de 1024 x 768 minimale et la taille de la boîte de dialogue initiale ne doit pas dépasser 900 x 700 pixels. Les boîtes de dialogue peuvent être redimensionnables, mais il n’est pas obligatoire.  
  
Il existe deux recommandations pour les boîtes de dialogue redimensionnables :  
  
1.  Qu’une taille minimale est définie pour la boîte de dialogue qui vous permettra d’optimiser pour le contrôle définir sans découpage, puis ajustez pour prendre en compte la croissance de localisation raisonnable.  
  
2.  Que la taille de la mise à l’échelle utilisateur persiste d’une session à l’autre. Par exemple, si l’utilisateur redimensionne une boîte de dialogue 150 %, un lancement suivant de la boîte de dialogue affichera de 150 %.  
  
#### <a name="position"></a>Position  
Les boîtes de dialogue doivent apparaître centrés dans l’IDE au premier lancement. La dernière position de boîtes de dialogue non redimensionnable n’a pas besoin être rendu persistant, et ils s’affichent centrés sur les démarrages suivants. 

Pour les boîtes de dialogue redimensionnables, la taille doit être persistante sur lancements ultérieurs. Pour les boîtes de dialogue modales redimensionnables, la position ne doit être persistants. Leur affichage centrée dans l’IDE empêche la possibilité de la boîte de dialogue qui apparaissent dans une position imprévisible ou inutilisable lors de la configuration de l’affichage de l’utilisateur a changé. 

Des boîtes de dialogue non modales qui peuvent être repositionnés, position de l’utilisateur doit être conservée sur lance suivantes, comme la boîte de dialogue peut-être être utilisé en tant que partie intégrante d’un flux de travail plus volumineux.  
  
Lorsque les boîtes de dialogue doivent générer d’autres boîtes de dialogue, la boîte de dialogue au premier plan doit mettre en cascade vers la droite et vers le bas à partir du parent de sorte qu’il évidente à l’utilisateur que vous leur avez accédé à un nouvel emplacement.  
  
#### <a name="modality"></a>Modalité  
En cours de modal signifie que les utilisateurs sont requis pour terminer ou annuler la boîte de dialogue avant de continuer. Étant donné que les boîtes de dialogue modales bloquent l’utilisateur d’interagir avec d’autres parties de l’environnement, les flux de tâches de votre fonctionnalité les utiliser avec parcimonie que possible. Lorsqu’une opération modale est nécessaire, Visual Studio possède un nombre de boîtes de dialogue partagées dans que vous pouvez intégrer des fonctionnalités. Si vous devez créer une nouvelle boîte de dialogue, suivez le modèle d’interaction d’une boîte de dialogue existant ayant des fonctionnalités similaires.  
  
Lorsque les utilisateurs ont besoin effectuer les deux activités à la fois, comme **trouver** et **remplacer** lors de l’écriture de nouveau code, la boîte de dialogue doit être non modale afin que l’utilisateur peut basculer facilement entre eux. Visual Studio utilise généralement des fenêtres Outil pour ce type de prise en charge de l’éditeur de tâche liée.  
  
#### <a name="control-configuration"></a>Configuration de contrôle  
Être compatible avec les configurations de contrôle existant qui accomplissent la même chose dans Visual Studio.  
  
#### <a name="title-bars"></a>Barres de titre  
  
-   Le texte dans la barre de titre doit refléter le nom de la commande qui a lancé.  
  
-   Aucune icône ne doit être utilisé dans les barres de titre de boîte de dialogue. Dans les cas où le système requiert un, utilisez le logo de Visual Studio.  
  
-   Les boîtes de dialogue ne doivent pas avoir réduire ou agrandir des boutons.  
  
-   Boutons d’aide dans la barre de titre ont été déconseillées. N’ajoutez pas les boîtes de dialogue Nouveau. Lorsqu’ils n’existent pas, ils doivent lancer une rubrique d’aide sur le plan conceptuel correspondant à la tâche.  
  
 ![Spécifications des indications pour les barres de titre dans les boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Spécifications des indications pour les barres de titre dans les boîtes de dialogue Visual Studio
  
#### <a name="control-buttons"></a>Boutons de commande  
En général, **OK**, **Annuler**, et **aide** boutons doivent être organisés horizontalement dans le coin inférieur droit de la boîte de dialogue. L’autre pile verticale est autorisée si une boîte de dialogue a plusieurs autres boutons au bas de la boîte de dialogue présente visual toute confusion avec les boutons du contrôle.  
  
![Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurations acceptables pour les boutons de contrôle dans les boîtes de dialogue Visual Studio
  
La boîte de dialogue doit inclure un bouton de contrôle par défaut. Pour déterminer la meilleure commande à utiliser en tant que la valeur par défaut, choisissez parmi les options suivantes (répertoriées par ordre de priorité) :  
  
-   Choisissez la commande plus sûre et plus sécurisée en tant que la valeur par défaut. Cela signifie en choisissant la commande plus susceptible d’empêcher la perte de données et accès au système inattendus.  
  
-   Si la sécurité et la perte de données ne sont pas des facteurs, puis choisissez la commande par défaut basée sur plus de commodité. Y compris la commande la plus probable en tant que la valeur par défaut améliorera les flux de travail de l’utilisateur lors de la boîte de dialogue prend en charge des tâches fréquentes ou répétitives.  
  
Évitez de choisir une action destructrice définitivement pour la commande par défaut. Si une commande est présente, choisissez une commande plus sûre que la valeur par défaut.  
  
#### <a name="access-keys"></a>Touches d’accès rapide  
N’utilisez pas de clés d’accès de **OK**, **Annuler**, ou **aide** boutons. Ces boutons sont mappés aux touches de raccourci par défaut :  
  
| Nom du bouton | Raccourci clavier |  
| --- | --- |  
| OK | Entrée |  
| Annuler | Échap |  
| Help | F1 |  
  
#### <a name="imagery"></a>IMAGERIE  
Utiliser des images avec parcimonie dans les boîtes de dialogue. N’utilisez pas de grandes icônes dans les boîtes de dialogue simplement à utiliser un espace. Utiliser des images uniquement si elles sont une partie importante de faire passer le message à l’utilisateur, telles que des icônes d’avertissement ou d’animations d’état.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a> Définition des priorités et la superposition  
  
#### <a name="prioritizing-your-ui"></a>Priorité de votre interface utilisateur  
Il peut être nécessaire de mettre certains éléments d’interface utilisateur au premier plan et placer le comportement plus avancée et les options (y compris les commandes obscurs) dans les boîtes de dialogue. Mettre les fonctionnalités couramment utilisées au premier plan en place pour celui-ci et en le rendant visible par défaut dans l’interface utilisateur avec une étiquette de texte lorsque la boîte de dialogue est affichée.  
  
#### <a name="layering-your-ui"></a>Superposition de votre interface utilisateur  
Si vous avez déterminé qu’une boîte de dialogue n’est nécessaire, mais les fonctionnalités connexes que vous souhaitez présenter à l’utilisateur va au-delà de ce qui peut être affiché dans la boîte de dialogue simple, vous devez votre interface utilisateur de la couche. Les méthodes les plus courantes de superposition que Visual Studio utilise sont des onglets et des couloirs ou des tableaux de bord. Dans certains cas, les zones qui peuvent être développés ou réduits peuvent convenir. Interface utilisateur adaptative n’est généralement pas recommandé dans Visual Studio.  
  
Présente des avantages et inconvénients des différentes méthodes de superposition de l’interface utilisateur via les contrôles d’onglet. Passez en revue la liste ci-dessous pour vous assurer que vous choisissez une technique de superposition qui convient à votre situation.  
  
##### <a name="tabbing"></a>Tabulation  
  
| Mécanisme de commutation | Avantages et utilisation appropriée | Utilisation inappropriée et inconvénients |  
| --- | --- | --- |  
| Contrôle Tab | Regrouper logiquement les pages de boîte de dialogue connexes<br /><br />Utile pour moins de cinq (ou le nombre d’onglets qui tiennent dans une ligne dans la boîte de dialogue) pages de contrôles connexes dans la boîte de dialogue<br /><br />Onglet étiquettes doivent être courtes : un ou deux mots qui peuvent d’identifier facilement le contenu<br /><br />Un style de boîte de dialogue système commun<br /><br />Exemple : **Explorateur de fichiers &gt; propriétés d’un élément** | Des étiquettes descriptives courts peut être difficile<br /><br />En règle générale n’évolue pas au-delà de cinq onglets dans une boîte de dialogue<br /><br />Inapproprié si vous avez trop d’onglets pour une ligne (utilisez une technique de remplacement de superposition)<br /><br />Non extensible |  
| Navigation avec barre latérale | Dispositif de commutation simple qui peut contenir plusieurs catégories à onglets<br /><br />Liste plate de catégories (sans hiérarchie)<br /><br />Extensible<br /><br />Exemple : **personnaliser... &gt; Ajouter des commandes** | Pas d’une utilisation optimale de l’espace horizontal s’il existe moins de trois groupes<br /><br />Tâche peut-être être mieux adapté à une liste déroulante. |  
| Contrôle Tree | Permet de catégories illimités<br /><br />Permet de regroupement et/ou de la hiérarchie de catégories<br /><br />Extensible<br /><br />Exemple : **outils &gt; Options** | Hiérarchies fortement imbriquées peuvent entraîner un défilement horizontal excessive<br /><br />Visual Studio propose une overabundance de vues d’arborescence |  
| Assistant | Grâce à la fin de la tâche guider l’utilisateur à travers les étapes séquentielles, tâche : l’Assistant représente une tâche de niveau supérieur et les panneaux individuels représentent des sous-tâches nécessaires pour accomplir la tâche globale<br /><br />Utile lors de la tâche dépasse les limites de l’interface utilisateur, comme lorsque l’utilisateur aurait autrement utiliser plusieurs éditeurs et fenêtres pour terminer la tâche<br /><br />Utile lors de la tâche nécessite la création de branche<br /><br />Utile lors de la tâche contient des dépendances entre les étapes<br /><br />Utile quand plusieurs tâches similaires avec la branche d’un arbre de décision peuvent être présentées dans une boîte de dialogue pour réduire le nombre de différentes boîtes de dialogue similaire | Inapproprié pour toute tâche qui ne nécessite pas un workflow séquentiel<br /><br />Les utilisateurs peuvent devenir submergé et par un Assistant avec trop d’étapes<br /><br />Assistants sont limitée, par nature, l’espace d’écran |  
  
##### <a name="hallways-or-dashboards"></a>Couloirs ou tableaux de bord  
Couloirs et tableaux de bord est les boîtes de dialogue ou les panneaux qui font Office de lancement pointe vers les autres boîtes de dialogue et windows. Le « couloir » bien conçu surfaces immédiatement uniquement les plus courantes options, commandes et paramètres, permettant à l’utilisateur de facilement accomplir des tâches courantes. Comme un couloir réelle fournit les guichets pour accéder aux salles derrière les, ici l’interface utilisateur moins courants est collectée dans distinct « locaux » (souvent autres boîtes de dialogue) de fonctionnalités connexes qui sont accessibles à partir de l’utilisateur principal.  
  
Vous pouvez également une interface utilisateur qui offre toutes les fonctionnalités disponibles dans une collection unique plutôt que la fonctionnalité moins courants dans des emplacements distincts de refactorisation est simplement un tableau de bord.  
  
![Concept de couloir pour exposer une interface utilisateur supplémentaire dans Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concept de couloir pour exposer une interface utilisateur supplémentaire dans Outlook
  
##### <a name="adaptive-ui"></a>Interface utilisateur adaptative  
Affichage ou masquage de l’interface utilisateur basée sur l’utilisation ou non signalé expérience d’un utilisateur est une autre façon de présenter l’interface utilisateur tout en masquant les autres parties. Cela n’est pas recommandée dans Visual Studio, comme les algorithmes pour le choix du moment afficher ou masquer l’interface utilisateur peuvent être difficile, et les règles ne sera toujours incorrect pour un jeu de cas.  
  
##  <a name="BKMK_Projects"></a> Projets  
  
### <a name="projects-in-the-solution-explorer"></a>Projets dans l’Explorateur de solutions  
La plupart des projets sont classées en fonction de référence, basée sur Active ou mixte. Les trois types de projets sont pris en charge simultanément dans l’Explorateur de solutions. La racine de l’expérience utilisateur à l’utilisation des projets s’effectue à l’intérieur de cette fenêtre. Bien que les nœuds de projets différentes soient référence, répertoire ou des projets de type de mode mixte, il est un modèle d’interaction commun qui doit être appliqué comme point de départ avant divergent en modèles d’utilisateur spécifiques à un projet.  
  
Les projets doivent toujours :  
  
-   Prise en charge la possibilité d’ajouter des dossiers pour organiser le contenu du projet du projet  
  
-   Mettre à jour un modèle cohérent pour la persistance d’un projet  
  
Projets doivent également conserver des modèles d’interaction cohérent pour :  
  
-   Suppression d’éléments de projet  
  
-   Enregistrer des documents  
  
-   Modification des propriétés de projet  
  
-   Modifiez le projet dans un autre affichage  
  
-   Opérations de glisser-déplacer  
  
### <a name="drag-and-drop-interaction-model"></a>Modèle d’interaction de glisser-déplacer  
Projets classer généralement eux-mêmes en tant que la base de référence (en mesure de conserver uniquement les références aux éléments de projet dans le stockage), (en mesure de conserver les éléments de projet uniquement physiquement stockées dans une hiérarchie de projet), basée sur les active ou mixte (capable de conserver des références éléments matériels ou physiques). L’IDE gère tous les trois types de projets simultanément dans le **l’Explorateur de solutions**.  
  
À partir d’un point de vue de glisser-déplacer, les caractéristiques suivantes doivent s’appliquer à chaque type de projet dans le **l’Explorateur de solutions**:  
  
-   **Projet de référence :** le point essentiel est que le projet fait glisser autour d’une référence à un élément dans le stockage. Lorsqu’un projet basé sur une référence agit comme une source pour une opération de déplacement, il doit supprimer uniquement la référence à l’élément dans le projet. L’élément ne doit pas réellement supprimé du disque dur. Lorsqu’un projet basé sur une référence agit comme une cible pour une opération de déplacement (ou copie), il doit ajouter une référence à l’élément source d’origine sans avoir à apporter une copie privée de l’élément.  
  
-   **Basé sur le répertoire de projet :** du point de vue du glisser-déplacer, le projet fait glisser autour de l’élément physique plutôt qu’une référence. Lorsqu’un projet basé sur le répertoire agit comme une source pour une opération de déplacement, elle doit finir la suppression de l’élément physique du disque dur, ainsi que de supprimer à partir du projet. Lorsqu’un projet basé sur le répertoire agit comme une cible pour une opération de déplacement (ou copie), qu’il doit rendre une copie de l’élément source à son emplacement cible.  
  
-   **Projet cible mixte :** du point de vue du glisser-déplacer, le comportement de ce type de projet est basé sur la nature de l’élément déplacé (il s’agit d’une référence à un élément dans le stockage) ou l’élément lui-même. Le comportement correct des références et les éléments physiques décrites ci-dessus.  
  
Si elle n'existait qu’un seul type de projet dans le **l’Explorateur de solutions**, les opérations de glisser-déplacer est simples. Étant donné que chaque système de projet a la possibilité de définir son propre comportement de glisser-déplacer, certaines instructions (basées sur le comportement de glisser-déplacer de l’Explorateur Windows) doivent être suivies pour garantir une expérience utilisateur prévisible :  
  
-   Opération de glissement un non modifié le **l’Explorateur de solutions** (lorsque ni Ctrl ni les touches MAJ sont enfoncés) devraient se traduire par une opération de déplacement.  
  
-   L’opération de glissement de décalage doit également entraîner une opération de déplacement.  
  
-   L’opération de glissement de CTRL doit aboutir à une opération de copie.  
  
-   Systèmes de projet basé sur la référence et mixte prend en charge la notion d’ajout d’un lien (ou référence) vers l’élément source. Lorsque ces projets sont la cible d’une opération de glisser-déplacer (lorsque **Ctrl + Maj +** est maintenu enfoncé), cela doit entraîner une référence à l’élément à ajouter au projet  
  
Toutes les opérations de glisser-déplacer sont cohérent entre les combinaisons de projets basée sur une référence basée sur Active et mixtes. En particulier, il pose se font passer pour autoriser une opération de déplacement entre une source basée sur le répertoire de projet et cible basée sur la référence, car le projet basé sur le répertoire de source aura supprimer l’élément source à la fin du déplacement. Le projet de base de référence cible puis obtenez une référence à un élément supprimé.  
  
Il est également trompeur de se font passer pour autoriser une opération de copie entre ces types de projets, car le projet de base de référence cible ne doit pas faire une copie indépendante de l’élément source. De même, Ctrl + Maj en faisant glisser vers un projet basé sur le répertoire de la cible ne doit pas être autorisé, car un projet basé sur le répertoire ne peut pas conserver des références. Dans les cas où l’opération de glisser-déplacer n’est pas pris en charge, l’IDE doit interdire la suppression et afficher le curseur ne (indiqué dans le tableau de pointeur ci-dessous) pour l’utilisateur.  
  
Pour implémenter correctement un comportement de glisser-déplacer, le projet source de l’opération glisser doit communiquer sa nature vers le projet cible. (Par exemple, s’il référence - ou basée sur Active ?) Cette information est indiquée par le format de Presse-papiers offertes par la source. En tant que la source de glissement (ou opération de copie du Presse-papiers) un projet doit offrir `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS` respectivement, selon si le projet est basé sur le répertoire ou référence. Les deux de ces formats ont le même contenu de données, ce qui est similaire aux fenêtres `CF_HDROP` mettre en forme, sauf que les listes de chaînes, au lieu d’être des noms de fichiers, sont un double -`NULL` arrêté la liste des `Projref` chaînes (tel que retourné par `IVsSolution::GetProjrefOfItem`ou `::GetProjrefOfProject` selon le cas).  
  
En tant que cible de dépôt (ou opération de collage dans le Presse-papiers), un projet doit accepter tous les deux `CF_VSREFPROJECTITEMS` et `CF_VSSTGPROJECTITEMS`, même si la gestion exacte de l’opération de glisser-déposer varie selon la nature du projet cible et le projet source. Le projet source déclare la nature, si elle offre `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS`. La cible de la liste déroulante comprend ses propres nature et par conséquent possède suffisamment d’informations pour prendre des décisions en tant que si un déplacement, la copie, ou lien doit être effectué. L’utilisateur modifie également l’opération de glisser-déplacer doit être effectuée en appuyant sur les Ctrl, MAJ, ou les touches Ctrl et MAJ. Il est important pour la cible de dépôt pour correctement indiquer quelle opération sera effectuée à l’avance dans son `DragEnter` et `DragOver` méthodes. Le **l’Explorateur de solutions** détermine automatiquement si le projet source et la cible sont le même projet.  
  
En faisant glisser des éléments de projet entre les instances de Visual Studio (par exemple, à partir d’une instance de devenv.exe vers un autre) n’est pas pris en charge. Le **l’Explorateur de solutions** directement désactive ce.  
  
L’utilisateur doit toujours être en mesure de déterminer l’effet d’une opération de glisser-déplacer en sélectionnant un élément, en le faisant glisser vers l’emplacement cible et en observant parmi les pointeurs de souris suivant s’affiche avant la suppression de l’élément :  
  
| Pointeur de la souris | Commande | Description |  
| :---: | --- | --- |  
| ![« Aucun dépôt » icône de souris](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Aucune suppression | Élément ne peut pas être déposé à l’emplacement spécifié. |  
| ![Icône de souris « copier »](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copier | Élément sera copié vers l’emplacement cible. |  
| ![Icône de souris « déplacer »](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Déplacement | Élément sera déplacé vers l’emplacement cible. |  
| ![Icône de souris « ajouter une référence »](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Ajouter une référence | Une référence à l’élément sélectionné sera ajoutée à l’emplacement cible. |

#### <a name="reference-based-projects"></a>projets basés sur une référence  
 Le tableau suivant récapitule les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets de cible basée sur référencé :  
  
| Modificateur | Category | Élément source : lien de référence / | Élément source : élément ou le fichier physique du système (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Aucun modificateur | Action | Déplacement | Lien |  
| Aucun modificateur | une cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |  
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Conserve l’élément d’origine |  
| Aucun modificateur | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |  
| Maj + glisser | Action | Déplacement | Aucune suppression |  
| Maj + glisser | une cible | Ajoute la référence à l’élément d’origine | Aucune suppression |  
| Maj + glisser | Source | Référence de suppressions à l’élément d’origine | Aucune suppression |  
| Maj + glisser | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | Aucune suppression |  
| CTRL + glisser | Action | Copier | Aucune suppression |  
| CTRL + glisser | une cible | Ajoute la référence à l’élément d’origine | Aucune suppression |  
| CTRL + glisser | Source | Conserve la référence à l’élément d’origine | Aucune suppression |  
| CTRL + glisser | Résultat | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | Aucune suppression |  
| Ctrl + Maj + glisser | Action | Lien | Lien |  
| Ctrl + Maj + glisser | une cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |  
| Ctrl + Maj + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |  
| Ctrl + Maj + glisser | Résultat | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_LINK` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |  
| Ctrl + Maj + glisser | Remarque | Identique au comportement de glisser-déplacer pour les raccourcis dans l’Explorateur Windows. ||  
| Couper/coller | Action | Déplacement | Lien |  
| Couper/coller | une cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |  
| Couper/coller | Source | Conserve la référence à l’élément d’origine|Conserve l’élément d’origine |  
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |  
| Copier/coller. | Action | Copier | Lien |  
| Copier/coller. | Source | Ajoute la référence à l’élément d’origine | Ajoute la référence à l’élément d’origine |  
| Copier/coller. | Résultat | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |  
| Copier/coller. | Action | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |  
  
#### <a name="directory-based-projects"></a>Projets basés sur le répertoire  
Le tableau suivant récapitule les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets de cible basée sur le répertoire :  
  
| Modificateur | Category | Élément source : lien de référence / | Élément source : élément ou le fichier physique du système (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Aucun modificateur | Action | Déplacement | Déplacement |  
| Aucun modificateur | une cible | Élément de copies à l’emplacement cible | Élément de copies à l’emplacement cible |  
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Référence de suppressions à l’élément d’origine | | Aucun modificateur | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |  
| Maj + glisser | Action | Déplacement | Déplacement |  
| Maj + glisser | une cible | Élément de copies à l’emplacement cible | Élément de copies à l’emplacement cible |  
| Maj + glisser | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Maj + glisser | Résultat | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |  
| CTRL + glisser | Action | Copier | Copier |  
| CTRL + glisser | une cible | Élément de copies à l’emplacement cible | Élément de copies à l’emplacement cible |  
| CTRL + glisser | Source | Conserve la référence à l’élément d’origine | Conserve la référence à l’élément d’origine |  
| CTRL + glisser | Résultat | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_COPY` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |  
| Ctrl + Maj + glisser | | Aucune suppression | Aucune suppression |  
| Couper/coller | Action | Déplacement | Déplacement |  
| Couper/coller | une cible | Élément de copies à l’emplacement cible | Élément de copies à l’emplacement cible |  
| Couper/coller | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |  
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément est supprimé de l’emplacement d’origine dans le stockage |  
| Copier/coller. | Action | Copier | Copier |  
| Copier/coller. | une cible | Ajoute la référence à l’élément d’origine | Élément de copies à l’emplacement cible |  
| Copier/coller. | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |  
| Copier/coller. | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans le stockage ins l’emplacement d’origine |
  
#### <a name="mixed-target-projects"></a>Projets cibles mixte  
Le tableau suivant récapitule les opérations de glisser-déplacer (ainsi que de couper/copier/coller) qui doivent être effectuées en fonction de la nature de l’élément et le modificateur clés source enfoncé pour les projets de cible mixte :  
  
| Modificateur | Category | Élément source : lien de référence / | Élément source : élément ou le fichier physique du système (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Aucun modificateur | Action | Déplacement | Déplacement |
| Aucun modificateur | une cible | Ajoute la référence à l’élément d’origine | Élément de copies à l’emplacement cible |
| Aucun modificateur | Source | Référence de suppressions à l’élément d’origine | Référence de suppressions à l’élément d’origine |
| Aucun modificateur | Résultat | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et de l’élément est supprimé de l’emplacement d’origine dans le stockage |
| Maj + glisser | Action | Déplacement | Déplacement |
| Maj + glisser | une cible | Ajoute la référence à l’élément d’origine | Élément de copies à l’emplacement cible |
| Maj + glisser | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine | 
| Maj + glisser | Résultat | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ MOVE` est retourné en tant qu’action de `::Drop` et de l’élément est supprimé de l’emplacement d’origine dans le stockage |
| CTRL + glisser | Action | Copier | Copier |
| CTRL + glisser | une cible | Ajoute la référence à l’élément d’origine | Élément de copies à l’emplacement cible |
| CTRL + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| CTRL + glisser | Résultat | `DROPEFFECT_ COPY` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ COPY` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Ctrl + Maj + glisser | Action | Lien | Lien |
| Ctrl + Maj + glisser | une cible | Ajoute la référence à l’élément d’origine | Ajoute la référence à un élément de la source d’origine |
| Ctrl + Maj + glisser | Source | Conserve la référence à l’élément d’origine | Conserve l’élément d’origine |
| Ctrl + Maj + glisser | Résultat | `DROPEFFECT_ LINK` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage | `DROPEFFECT_ LINK` est retourné en tant qu’action de `::Drop` et de l’élément reste dans l’emplacement d’origine dans le stockage |
| Couper/coller | Action | Déplacement | Déplacement |
| Couper/coller | une cible | Élément de copies à l’emplacement cible | Élément de copies à l’emplacement cible |
| Couper/coller | Source | Référence de suppressions à l’élément d’origine | Supprime l’élément à partir de l’emplacement d’origine |
| Couper/coller | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément est supprimé de l’emplacement d’origine dans le stockage |
| Copier/coller. | Action | Copier | Copier |
| Copier/coller. | une cible | Ajoute la référence à l’élément d’origine | Élément de copies à l’emplacement cible |
| Copier/coller. | Source | Conserve l’élément d’origine | Conserve l’élément d’origine |
| Copier/coller. | Résultat | Élément reste dans l’emplacement d’origine dans le stockage | Élément reste dans l’emplacement d’origine dans le stockage |
  
Ces détails doivent être prises en considération lors de l’implémentation en faisant glisser le **l’Explorateur de solutions**:  
  
-   Conception pour plusieurs scénarios de sélection.  
  
-   Noms de fichiers (chemin d’accès complet) doivent être uniques dans le projet cible ou la suppression n’est pas autorisée.  
  
-   Les noms de dossier doivent être uniques (non-respect de la casse) au niveau qu’ils sont en cours de suppression.  
  
-   Il existe des différences de comportement entre les fichiers qui sont ouverts ou fermés au moment de faire glisser (non mentionnée dans les scénarios ci-dessus).  
  
-   Fichiers de niveau supérieur se comportent différemment des fichiers dans les dossiers.  
  
Un autre problème à connaître est la gestion des opérations de déplacement des éléments qui ont des éditeurs ou les concepteurs ouverts. Le comportement attendu est le suivant (s’applique à tous les types de projet) :  
  
1.  Si l’éditeur ouvrir/le concepteur n’a pas les modifications non enregistrées, la fenêtre d’éditeur/concepteur doit être fermée en mode silencieux.  
  
2.  Si l’éditeur ouvrir/le concepteur n’a pas les modifications non enregistrées, la source de l’opération glisser doit attendre pour la liste déroulante pour se produire puis demandez à l’utilisateur d’enregistrer les modifications non validées dans les documents ouverts avant de fermer la fenêtre avec un message semblable au suivant :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Ainsi, l’utilisateur la possibilité d’enregistrer le travail en cours avant la cible met ses copies. Une nouvelle méthode `IVsHierarchyDropDataSource2::OnBeforeDropNotify` a été ajoutée pour permettre cette gestion.  
  
La cible de copie de l’état de l’élément car il est dans le stockage (n’incluant ne pas les modifications non enregistrées dans l’éditeur si l’utilisateur a choisi **non**). Une fois la cible a terminé sa copie (dans `IVsHierarchyDropDataSource::Drop`), la source doit avoir la possibilité pour terminer la partie de la suppression de l’opération de déplacement (dans `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Les éditeurs avec des modifications non enregistrées doivent être laissés ouverts. Pour les documents avec des modifications non enregistrées, cela signifie que la partie de la copie de l’opération de déplacement sera effectuée, mais la partie de la suppression va être abandonnée. Dans un scénario de sélection de plusieurs lorsque l’utilisateur choisit **non**, ces documents avec des modifications non enregistrées ne doivent pas fermés ou supprimés, mais celles sans modifications non enregistrées doivent être fermés et supprimés.
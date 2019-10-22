---
title: Page Options, Environnement, propriétés de nœud | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c7b6370793068ff07f30066ddd51b72dcc924b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668702"
---
# <a name="options-page-environment-node-properties"></a>Page Options, Environnement, propriétés de nœud
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ce document décrit les pages (ou collections de propriétés) associées à la catégorie **Environnement**, `DTE.Properties("Environment", <Property Page>)`, de la boîte de dialogue **Options**. Le titre de chaque sous-section correspond à l’appel utilisé pour accéder à la collection de propriétés, tandis que le tableau dans chaque sous-section répertorie les propriétés de la collection.

## <a name="general"></a>Général
 `DTE.Properties("Environment", "General")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (booléen)|Détermine si la barre d'état est visible.|
|WindowMenuContainsNItems|Get/Set (Short)|Détermine comment les fenêtres de document sont contenues dans le bas du menu Fenêtres.|
|MRUListContainsNItems|Get/Set (Short)|Détermine le nombre de fichiers affichés dans le sous-menu Les dernières utilisées.|
|Animations|Get/Set (booléen)|Détermine si l'environnement de développement intégré (IDE) utilise des animations dans la barre d'état.|
|AnimationSpeed|Get/Set (Short)||
|AutoAdjustExperience|Get/Set (booléen)|Ajuste automatiquement l'expérience visuelle selon les performances du client.|
|RichClientExperienceOptions|Get/Set (Enum)|Active l'expérience visuelle améliorée avec des valeurs dans <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (booléen)|Détermine si le bouton **Fermer** est affiché seulement sous l’onglet actif.|
|AutohidePinActiveTabOnly|Get/Set (booléen)|Détermine si le bouton **Masquer automatiquement** affecte seulement l’onglet actif.|

## <a name="add-inmacros-security"></a>Sécurité des compléments/macros
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|MacrosEnabled|Get/Set (booléen)|Permet l'exécution des macros.|
|AddinsEnabled|Get/Set (booléen)|Permet le chargement des compléments.|
|LoadAddinsFromTheWeb|Get/Set (booléen)|Permet le chargement des compléments à partir d'une URL sur le web.|

## <a name="documents"></a>Documents
 `DTE.Properties("Environment", "Documents")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (booléen)|Détermine si l'ouverture d'un nouveau fichier réutilise la fenêtre de document active si le document actif est enregistré. `false` signifie toujours ouvrir une nouvelle fenêtre de document pour chaque document ouvert.|
|DetectFileChangesOutsideIDE|Get/Set (booléen)|Détermine si l'environnement recharge automatiquement les fichiers ouverts dans l'IDE quand le système d'exploitation signale à l'IDE que les fichiers ont été modifiés sur le disque.|
|AutoloadExternalChanges|Get/Set (booléen)|Détermine si des modifications externes détectées sur des documents ouverts rechargent automatiquement le fichier modifié si le document ouvert n'est pas modifié. Si le document ouvert est modifié et que cette propriété est `true`, l'IDE pose la question à l'utilisateur, comme si cette propriété était `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (booléen)|Détermine si la commande <xref:EnvDTE.DTEClass.OpenFile%2A> renseigne le nom du répertoire et du fichier à partir du dernier document actif ou à partir du dernier emplacement où vous avez ouvert un fichier.|
|MiscFilesProjectSavesLastNItems|Get/Set (Short)|Détermine le nombre de fichiers enregistrés par le projet Fichiers divers. En conséquence, vous pouvez voir ce que vous avez ouvert en dernier sous forme de fichier divers sur le disque lors de la prochaine utilisation de l'IDE.|
|ShowMiscFilesProject|Get/Set (booléen)|Détermine si le projet Fichiers divers est affiché.|
|CheckForConsisentLineEndings|Get/Set (booléen)|Vérifie la cohérence des fins de ligne lors du chargement d'un fichier.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (booléen)|Enregistre les documents au format Unicode quand les données ne peuvent pas être enregistrées dans la page de codes.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (booléen)|Affiche un avertissement quand une annulation globale modifie d'autres fichiers modifiés.|
|AllowEditingReadOnlyFiles|Get/Set (booléen)|Autorise la modification des fichiers en lecture seule, mais affiche un avertissement lors de la tentative de les enregistrer.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Position dans l'onglet où insérer le document ouvert.|

## <a name="extension-manager"></a>Gestionnaire d’extensions
 `DTE.Properties("Environment", "ExtensionManager")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (booléen)|Charge les extensions par utilisateur quand Visual Studio est exécuté sous des informations d'identification d'administrateur. Visual Studio doit être redémarré après la modification de cette valeur.|
|EnableOnline|Get/Set (booléen)|Permet l'accès aux extensions sur la galerie Visual Studio.|
|AutomaticallyCheckForUpdates|Get/Set (booléen)|Recherche automatiquement les mises à jour des extensions installées.|

## <a name="find-and-replace"></a>Rechercher et remplacer
 `DTE.Properties("Environment", "FindAndReplace")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (booléen)|Affiche des messages d'avertissement.|
|InitializeFromEditor|Get/Set (booléen)|Remplit automatiquement la zone **Rechercher** avec du texte provenant de l’éditeur.|
|ShowMessageBoxes|Get/Set (booléen)|Affiche des messages d'information.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (booléen)|Masque la fenêtre **Rechercher et remplacer** une fois qu’une correspondance est trouvée à l’aide de **Recherche rapide** ou de **Remplacement rapide**.|

## <a name="import-and-export-settings"></a>Importation et exportation de paramètres
 `DTE.Properties("Environment", "Import and Export Settings")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (booléen)|Utilise les paramètres du fichier spécifié par TeamSettingsFile.|
|TeamSettingsFile|Get/Set (chaîne)|Nom du fichier qui a les paramètres d'équipe.|
|AutoSaveFile|Get/Set (chaîne)|Nom du fichier où les paramètres utilisateur sont automatiquement enregistrés.|

## <a name="international-settings"></a>Paramètres internationaux
 `DTE.Properties("Environment", "International")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|Langue|Get/Set (chaîne)|Valeur LCID pour la langue actuelle de Visual Studio.|

## <a name="keyboard"></a>Clavier
 `DTE.Properties("Environment", "Keyboard")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|Scheme|Get/Set (chaîne)|Retourne une chaîne qui contient un schéma intégré, une chaîne contenant le chemin d'accès complet du fichier .vsk qui est chargé, ou « (Par défaut) » si aucun fichier .vsk n'est chargé.|

## <a name="projects-and-solution"></a>Projets et solution
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Get/Set (chaîne)|Détermine si l'IDE enregistre tout avant un aperçu ou l'exécution d'un projet généré.|
|ProjectsLocation|Get/Set (chaîne)|Détermine le répertoire par défaut où la boîte de dialogue **Ajouter un projet** enregistre les nouveaux projets.|
|ShowOutputWindowBeforeBuild|Get/Set (booléen)|Détermine si le démarrage d’une build affiche la fenêtre **Sortie**.|
|ShowTaskListAfterBuild|Get/Set (booléen)|Détermine si une opération de build qui échoue affiche la **Liste des tâches** quand la build est terminée.|
|TrackFileSelectionInExplorer|Get/Set (booléen)|Détermine si l’élément actuel est suivi dans l’**Explorateur de solutions**.|
|AlwaysShowSolutionNode|Get/Set (booléen)|Détermine si le nœud de la solution est affiché.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (booléen)|Détermine si les opérations d'enregistrement sont limitées aux projets de démarrage et à leurs fichiers dépendants.|
|ShowAdvancedBuildConfigurations|Get/Set (booléen)|Détermine si les configurations de build avancées sont affichées.|
|ConcurrentBuilds|Get/Set (chaîne)|Détermine le nombre maximal de builds de projet qui peuvent être effectuées en parallèle.|
|SaveNewProjects|Get/Set (booléen)|Détermine si les nouveaux projets sont enregistrés automatiquement après avoir été créés.|
|PromptForRenameSymbol|Get/Set (booléen)|Spécifie s'il faut inviter l'utilisateur à utiliser des noms symboliques quand des fichiers sont renommés.|
|OnRunWhenErrors|Get/Set (Enum)|Spécifie le comportement à l'exécution quand une build se termine avec des erreurs.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Spécifie le comportement à l'exécution quand un projet est périmé.|
|ProjectTemplatesLocation|Get/Set (chaîne)|Répertoire qui contient les modèles de projets utilisateur.|
|ProjectItemTemplatesLocation|Get/Set (chaîne)|Répertoire qui contient les modèles d'éléments utilisateur.|
|DefaultBehaviorForStartupProjects|Get/Set (chaîne)||
|MSBuildOutputVerbosity|Get/Set (chaîne)|Spécifie le niveau de détail pour la sortie de la build.|

## <a name="startup"></a>Démarrage
 `DTE.Properties("Environment", "Startup")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Action à exécuter au démarrage, à partir de <xref:EnvDTE.vsStartUp>, avec des valeurs de 0 à 5 :<br /><br /> - 0 : Ouvrir la page d’accueil<br />- 1 : Charger la dernière solution chargée<br />- 2 : Afficher la boîte de dialogue **Ouvrir un projet**<br />- 3 : Afficher la boîte de dialogue **Nouveau projet**<br />- 4 : Afficher l’environnement vide<br />- 5 : Afficher la page de démarrage|
|StartPageRSSUrl|Get/Set (chaîne)|URL du flux RSS utilisé au démarrage.|
|StartPageRefreshDownloadedContent|Get/Set (booléen)|Actualise la page de démarrage après chaque passage de l'intervalle spécifié dans StartPageRefreshInterval.|
|StartPageRefreshInterval|Get/Set (Short)|Intervalle en minutes pour actualiser la page de démarrage.|

## <a name="tasklist"></a>TaskList
 `DTE.Properties("Environment", "TaskList")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (booléen)|Spécifie si une boîte de confirmation s’affiche quand des tâches dans le **Liste des tâches** sont supprimées.|
|WarnOnAddingHiddenItem|Get/Set (booléen)|Spécifie si vous recevez un avertissement lors de l'ajout d'une tâche utilisateur qui ne sera pas affichée.|
|DontShowFilePaths|Get/Set (booléen)|Spécifie si les chemins d'accès complets des fichiers sont affichés dans la liste des tâches.|
|CommentTokens|SafeArray|Retourne un SafeArray des valeurs de jeton de commentaire. Chacun a les champs `Name` (chaîne) et `Priority` (<xref:EnvDTE.vsTaskPriority>, Haute, Moyenne ou Faible).|

## <a name="web-browser"></a>Navigateur web
 `DTE.Properties("Environment", "WebBrowser")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|HomePage|Get/Set (chaîne)|Représente l'URL de la page d'accueil.|
|SearchPage|Get/Set (chaîne)|Représente l'URL de la page de recherche.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Source, Conception, Externe).|
|ViewSourceExternalProgram|Get/Set (chaîne)|Chemin d’accès de la visionneuse de la source externe.|

## <a name="see-also"></a>Voir aussi
 [Contrôle des options paramètres](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [détermination des noms des éléments de propriété dans les pages d’options](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [page Options, polices et couleurs nœud Propriétés](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [options, éditeur de texte Propriétés du nœud](../../ide/reference/options-page-text-editor-node-properties.md) [boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md) de l’environnement

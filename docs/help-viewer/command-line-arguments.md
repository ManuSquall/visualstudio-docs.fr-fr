---
title: Arguments de ligne de commande pour Help Content Manager
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e25e213f168739f6fe98d60a6ffbf00237a970b6
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "54406097"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Arguments de ligne de commande pour Help Content Manager

Vous pouvez spécifier la façon de déployer et de gérer le contenu d’aide locale avec des arguments de ligne de commande pour Help Content Manager (*HlpCtntMgr.exe*). Vous devez exécuter des scripts pour cet outil en ligne de commande avec des autorisations d’administrateur, et vous ne pouvez pas exécuter ces scripts en tant que service. Vous pouvez effectuer les tâches suivantes à l’aide de cet outil :

-   Ajouter ou mettre à jour le contenu d’aide locale à partir d’un disque ou du cloud.

-   Supprimer le contenu d’aide locale.

-   Déplacer le magasin de contenu d’aide locale.

-   Ajouter, mettre à jour, supprimer ou déplacer le contenu d’aide locale en mode silencieux.

Syntaxe :

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Par exemple :

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

## <a name="switches-and-arguments"></a>Commutateurs et arguments

Le tableau suivant définit les commutateurs et les arguments que vous pouvez utiliser pour l’outil en ligne de commande pour Help Content Manager :

|Basculer|Obligatoire ?|Arguments|
|------------|---------------|---------------|
|/operation|Oui|-   **Install** : ajoute des livres de la source d’installation spécifiée dans le magasin de contenu local.<br />     Ce commutateur requiert l’argument /booklist, l’argument /sourceURI, ou les deux. Si vous ne spécifiez pas l’argument /sourceURI, l’URI de Visual Studio par défaut est utilisé comme source d’installation. Si vous ne spécifiez pas l’argument /booklist, tous les livres sur /sourceUri sont installés.<br />-   **Uninstall** : supprime les livres que vous spécifiez dans le magasin de contenu local.<br />     Ce commutateur requiert l’argument /booklist ou l’argument /sourceURI.  Si vous spécifiez l’argument /sourceURI, tous les livres sont supprimés, et l’argument /booklist est ignoré.<br />-   **Move** : déplace le magasin local vers le chemin que vous spécifiez. Le chemin du magasin local par défaut est défini comme répertoire sous *%ProgramData%*<br />     Ce commutateur requiert les arguments /locationPath et /catalogName. Les messages d’erreur sont collectés dans le journal des événements si vous spécifiez un chemin non valide ou si le lecteur ne contient pas suffisamment d’espace libre pour accueillir le contenu.<br />-   **Refresh** : met à jour les rubriques qui ont été modifiées depuis leur installation ou récemment mises à jour.<br />     Ce commutateur requiert l’argument /sourceURI.|
|/catalogName|Oui|Spécifie le nom du catalogue de contenu.|
|/locale|Non|Spécifie les paramètres régionaux du produit utilisés pour afficher et gérer le contenu pour l’instance actuelle de la visionneuse d’aide. Par exemple, vous spécifiez `EN-US` pour Anglais (États-Unis).<br /><br /> Si vous ne spécifiez pas de paramètres régionaux, ceux du système d’exploitation sont utilisés. S’ils ne peuvent pas être déterminés, `EN-US` est utilisé.<br /><br /> Si vous spécifiez des paramètres régionaux non valides, un message d’erreur est collecté dans le journal des événements.|
|/e|Non|Élève Help Content Manager aux privilèges d’administrateur si l’utilisateur actuel dispose d’informations d’identification d’administration.|
|/sourceURI|Non|Spécifie l’URL à partir de laquelle le contenu est installé (API de service) ou le chemin du fichier d’installation du contenu (*.msha*). L’URL peut pointer vers le groupe de produits (nœud de niveau supérieur) ou les livres de produit (nœud de niveau document) dans un point de terminaison de style Visual Studio 2010. Il n’est pas nécessaire d’inclure une barre oblique (/) à la fin de l’URL. Si vous le faites tout de même, elle est gérée correctement.<br /><br /> Un message d’erreur est enregistré dans le journal des événements si vous spécifiez un fichier qui est introuvable, non valide ou inaccessible, ou si une connexion Internet n’est pas disponible ou est interrompue pendant la gestion du contenu.|
|/vendor|Non|Spécifie le constructeur pour le contenu du produit qui sera supprimé (par exemple, `Microsoft`). L’argument par défaut pour ce commutateur est Microsoft.|
|/productName|Non|Spécifie le nom du produit pour les livres qui seront supprimés. Le nom du produit est identifié dans les fichiers *helpcontentsetup.msha* ou *books.html* qui accompagnent le contenu. Vous pouvez supprimer des livres d’un seul produit à la fois. Pour supprimer des livres de plusieurs produits, vous devez exécuter plusieurs installations.|
|/booklist|Non|Spécifie les noms des livres à gérer, séparés par des espaces. Les valeurs doivent correspondre aux noms de livres indiqués sur le support d’installation.<br /><br /> Si vous ne spécifiez pas cet argument, tous les livres recommandés pour le produit indiqué dans /sourceURI sont installés.<br /><br /> Si le nom d’un livre contient un ou plusieurs espaces, encadrez-le de guillemets doubles (") afin que la liste soit délimitée correctement.<br /><br /> Les messages d’erreur sont stockés si vous spécifiez un argument /sourceURI non valide ou inaccessible.|
|/skuId|Non|Spécifie la référence SKU du produit depuis la source d’installation, puis filtre les livres que le commutateur /SourceURI identifie.|
|/membership|Non|-   **Minimum** : installe un ensemble minimum de contenu d’aide sur la référence que vous spécifiez à l’aide du commutateur /skuId. Le mappage entre le SKU et l’ensemble de contenu est exposé dans l’API de service.<br />-   **Recommended** : installe un ensemble de livres recommandés pour la référence que vous spécifiez à l’aide de l’argument /skuId. La source d’installation est l’API de service ou le *.MSHA*.<br />-   **Full** : installe le jeu complet de livres pour la référence que vous spécifiez à l’aide de l’argument /skuId. La source d’installation est l’API de service ou le *.MSHA*.|
|/locationpath|Non|Spécifie le dossier par défaut du contenu d’aide locale. Vous devez utiliser ce commutateur uniquement pour installer ou déplacer le contenu. Si vous spécifiez ce commutateur, vous devez également spécifier le commutateur /silent.|
|/silent|Non|Installe ou supprime le contenu d’aide sans questionner l’utilisateur ou afficher d’élément d’interface utilisateur tel que l’icône dans la zone de notification d’état. La sortie est stockée dans un fichier, dans le répertoire *%Temp%*. **Important :**  Pour installer le contenu en mode silencieux, vous devez utiliser les fichiers signés numériquement *.cab*, pas les fichiers *.mshc*.|
|/launchingApp|Non|Définit l’application et le contexte de catalogue lorsque la visionneuse d’aide est lancée sans application parente. Les arguments pour ce commutateur sont *CompanyName*, *ProductName* et *VersionNumber* (par exemple, `/launchingApp Microsoft,VisualStudio,15.0`).<br /><br /> Cet argument est requis pour installer le contenu avec le paramètre /silent.|
|/wait *secondes*|Non|Suspend les opérations d’installation, de désinstallation et d’actualisation. Si une opération est en cours pour le catalogue, le processus attend jusqu’au nombre donné de secondes pour continuer. Utilisez 0 pour une attente indéfinie.|
|/?|Non|Répertorie les commutateurs, ainsi que leur description, de l’outil en ligne de commande pour le gestionnaire de contenu d’aide.|

### <a name="exit-codes"></a>Codes de sortie

Lorsque vous exécutez l’outil en ligne de commande pour le gestionnaire de contenu d’aide en mode silencieux, il renvoie les codes de sortie suivants :

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>Voir aussi

- [Guide de l’administrateur Help Viewer](../help-viewer/administrator-guide.md)
- [Substitutions dans Help Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
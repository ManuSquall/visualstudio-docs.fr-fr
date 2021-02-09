---
title: VSPerfReport | Microsoft Docs
description: Découvrez que l’outil en ligne de commande VSPerfReport est utilisé pour créer des rapports à l’aide de Visual Studio Outils de profilage les fichiers de données de profilage.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 507ea5a90aa17ba252a95714f488f5ea22dff4f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911505"
---
# <a name="vsperfreport"></a>VSPerfReport
L’outil en ligne de commande VSPerfReport permet de créer des rapports à l’aide des fichiers de données des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le format de rapport par défaut est un fichier .*csv*.

 VSPerfReport utilise la syntaxe suivante :

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Notez que `filename` doit être un fichier .*vsp* ou .*vsps* valide.

 L’outil en ligne de commande VSPerfReport est également utilisé pour comparer des fichiers .*vsp* ou .*vsps*. Pour générer un rapport de différences (« diff »), utilisez la syntaxe suivante :

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` doivent être des fichiers .*vsp* ou .*vsps* valides.

## <a name="symbol-files"></a>Fichiers de symboles
 Pour afficher les informations de symbole telles que les noms de fonction et les numéros de ligne, VSPerfReport doit accéder aux fichiers de symboles (.PDB) des composants profilés et aux fichiers de symboles Windows. Pour plus d’informations, consultez [Guide pratique pour spécifier les emplacements du fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Options de rapport générales
 Le tableau suivant décrit les options générales de mise en forme de rapport et les options qui sélectionnent les données devant figurer dans le rapport.

|Options|Description|
|-------------|-----------------|
|**U**|La sortie du rapport et la sortie de la console redirigée sont écrites au format Unicode. Doit être la première option spécifiée.|
|**Summary:**[*types*]|Crée un ou plusieurs types de rapports.<br /><br /> -   `All` : tous les types de rapport sont générés.<br />-   `CallerCallee` : relations parent/enfant entre les fonctions.<br />-   `Function` : fonctions appelées.<br />-   `CallTree` : hiérarchie des fonctions appelées.<br />-   `Counter` : toutes les marques ainsi que les valeurs des compteurs de performances Windows.<br />-   `Ip` : instructions profilées.<br />-   `Life` : durée de vie des objets alloués (disponible lorsque les données d’allocation ont été collectées).<br />-   `Line` : données de profil de la ligne du code source.<br />-   `Header` : le rapport contient des informations d’en-tête de fichier.<br />-   `Mark` : toutes les marques.<br />-   `Module` : modules profilés.<br />-   `Process` : processus profilés.<br />-   `Thread` : threads profilés.<br />-   `Type` : types alloués.<br />-   `Contention` : contentions de ressource.<br />-   `RuleWarnings` : problèmes de règles de performance.<br />-   `ETW` : tous les événements de suivi d’événements pour Windows (ETW) collectés dans l’exécution du profilage. Le fichier de données .etl doit être à son emplacement d’origine ou dans le répertoire qui contient le fichier .vsp ou .vsps.|
|**Xml**|Rapport de sortie au format XML.|
|**CallTrace**|Crée une liste d’entrées et de sorties de fonction, d’événements ETW et de marques.|
|**ClearPackedSymbols**|Supprime les symboles précédemment incorporés d’un fichier de données du profileur. Exécutez cette commande avant d’exécuter PackSymbols une deuxième fois.|
|**SymbolPath :**`path`|Spécifie un ou plusieurs chemins de recherche ou serveurs de symboles qui contiennent les symboles pour le fichier de données du profileur.|
|**DebugSymPath**|Répertorie les emplacements dans lesquels la recherche des symboles est effectuée et indique si des symboles sont trouvés. Cette option est utile pour résoudre les problèmes de résolution de symboles.|
|**PackSymbols**|Enregistre les symboles dans le fichier de données de profilage (.vsp) pour que les fichiers de symboles (.*pdb*) ne soient pas nécessaires à l’analyse.|
|**Output:** *chemin*&#124;*nom_fichier*|Spécifie un autre emplacement pour les fichiers de rapport générés. Par défaut, les rapports sont créés dans le répertoire actif.|
|**SummaryFile**|Analyse et enregistre les informations analysées dans un fichier de résumé .vsps.|
|**PrintMarks**|Indique les noms et les horodatages pour toutes les marques du fichier de rapport spécifié.|
|**?**|Affiche des informations sur l’utilisation.|
|**NoLogo**|Masque les informations de version durant l’exécution du rapport.|
|**UserRulesDirectory**|Spécifie le répertoire qui contient les règles de performance définies par l’utilisateur [pas encore implémenté].|

## <a name="filter-options"></a>Options de filtre
 Le tableau suivant décrit les options permettant de filtrer les données disponibles.

|Options|Description|
|-------------|-----------------|
|**JustMyCode**[**:**[ `caller` ] [, `callee` ]]|Affiche uniquement les appels de fonction d’application utilisateur et masque les appels système.<br /><br /> -   Aucun paramètre : masque toutes les fonctions système.<br />-   `caller` : affiche un niveau de fonctions système qui appellent des fonctions d’application.<br />-   `callee` : affiche un niveau de fonctions système appelées par les fonctions d’application utilisateur.|
|**StartTime :**[*valeur*]|Affiche uniquement les données collectées après la valeur (en millisecondes).|
|**EndTime :**[*valeur*]|Affiche uniquement les données collectées avant la valeur (en millisecondes).|
|**FilterFile:** `VSPFFile`|Spécifie l’emplacement d’un fichier filtre qui a été généré à partir de la fenêtre Rapport de performances de Visual Studio.|
|**MsFilter :**[*StartTime, Duration*]|Affiche uniquement les données de `starttime` jusqu’à la fin de `duration` (en millisecondes).|
|**Processus :**[*PID*]|Affiche uniquement les données du processus spécifié.|
|**Thread :**[*ThreadID*]|Affiche uniquement les données du thread spécifié.|
|**Thread :**[*ThreadID, ProcessId*]|Affiche uniquement les données du thread spécifié associé au processus spécifié.|

## <a name="difference-report-options"></a>Options du rapport des différences
 Le tableau suivant décrit les options disponibles pour comparer des fichiers de rapport.

|Options|Description|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|Compare deux fichiers de rapports (.*vsp* ou .*vsps*). Les options de résumé sont ignorées à l’aide de l’option diff.|
|**Diff:**[*value*]|Au-dessous de cette valeur de seuil, la différence entre deux valeurs est ignorée. De même, les nouvelles données avec des valeurs en dessous de ce seuil ne sont pas affichées.|
|**DiffTable :**[*TableName*]|Utilise cette table spécifique pour comparer des fichiers. La valeur par défaut est la table des fonctions.|
|**DiffColumn :**[*ColumnName*]|Utilise cette colonne spécifique pour comparer des valeurs. La valeur par défaut est la colonne de pourcentage d’échantillons exclusifs.|
|**QueryDiffTables**|Affiche les tables et colonnes valides pour les deux fichiers de rapports fournis.|

## <a name="see-also"></a>Voir aussi
- [Vues des rapports de performances](../profiling/performance-report-views.md)

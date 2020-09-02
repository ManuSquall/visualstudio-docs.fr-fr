---
title: Comment-comparer des fichiers de données de performances | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5fdb8057823732503a215fb4f2c12ebee33b34c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330819"
---
# <a name="how-to-compare-performance-data-files"></a>Guide pratique pour comparer des fichiers de données de performances
Vous pouvez comparer les résultats de deux fichiers de données du profileur (.* vsp* ou. *vsps*) en créant un rapport de comparaison (« diff ») ou une vue. Le rapport de comparaison montre les différences, les régressions de performances et les améliorations qui se sont produites d’une session de profilage à l’autre.

 Le rapport Différences présente les données sous forme de tableau. Le tableau présente les données delta, c’est-à-dire ce qui a été modifié par rapport à la base de référence. Ces données sont calculées en déterminant la différence entre l’ancienne valeur, la valeur de base de référence et la valeur résultante de la nouvelle analyse.

 Les comparaisons des données du profileur peuvent être basées sur les fonctions du code, les modules de l’application, les lignes, les pointeurs d’instruction et les types.

 Vous pouvez définir un seuil pour réduire le bruit et exclure de l’affichage les lignes du tableau dont la valeur n’a pas changé de manière significative.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Pour créer une vue de comparaison de fichiers pour un projet dans l’Explorateur de performances

1. Dans **Explorateur de performances**, sous **rapports**, sélectionnez le. *vsp* ou. fichier de rapport *vsps* que vous souhaitez utiliser comme valeurs de référence pour la comparaison.

2. Sélectionnez le. *vsp* ou. fichiers de rapport *vsps* que vous souhaitez comparer.

3. Cliquez sur l’un des fichiers sélectionnés, puis cliquez sur **Comparer les rapports**.

### <a name="to-compare-values"></a>Pour comparer des valeurs

1. Sélectionnez l’onglet **Rapport de comparaison** dans la vue Rapport.

2. Dans la liste déroulante **Table**, sélectionnez les fonctions ou les modules à comparer.

3. Dans la liste déroulante **Colonne**, sélectionnez la valeur à comparer.

4. (facultatif) Tapez une valeur pour **Seuil**.

5. Cliquez sur **Appliquer**.

### <a name="to-compare-report-files"></a>Pour comparer des fichiers de rapport

1. Dans le menu **Analyser**, sélectionnez **Comparer les rapports de performances**.

2. Dans la fenêtre **Sélectionner les fichiers d’analyse pour la comparaison** , recherchez et sélectionnez le fichier d’analyse de fichier de **base** (.* vsp* ou. *vsps*) et le **fichier de comparaison** (.* vsp* ou. *vsps*).

3. Cliquez sur **OK**.

---
title: Enregistrement et exportation de données des outils d’analyse des performances | Microsoft Docs
description: Découvrez comment vous pouvez enregistrer des vues filtrées ou non filtrées de fichiers de données de profilage (. vsp) en tant que fichiers de rapports analysés (. vsps).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa43d324f23958c9dc9b72447527ecd035e99c53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950102"
---
# <a name="save-and-export-performance-tools-data"></a>Enregistrer et exporter les données des outils d’analyse des performances
Cet article décrit comment enregistrer et exporter des fichiers de données de performances.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Comment enregistrer des fichiers de données de performances en tant que fichiers de rapports analysés
 Vous pouvez enregistrer des vues filtrées ou non filtrées de données de profilage (.*vsp*) en tant que rapport analysé (.*vsps*). Un fichier de rapport analysé peut être affiché dans la fenêtre d’affichage des rapports et est beaucoup plus petit que l’original. fichier *vsp* . Toutefois, vous ne pouvez pas appliquer un filtre aux données d’un. fichier *vsps* . Vous pouvez créer un fichier de rapport analysé à partir de la Explorateur de performances sans ouvrir le fichier dans l’environnement de développement intégré (IDE), ou vous pouvez ouvrir et filtrer le. *vsp* , puis enregistrez les résultats.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Pour enregistrer un rapport de performances analysé à partir de l’Explorateur de performances

1. Sous **rapports**, cliquez avec le bouton droit sur le fichier de données de profilage que vous souhaitez analyser, puis cliquez sur **Enregistrer l’analyse**.

2. Dans la boîte de dialogue **Enregistrer les données analysées** , spécifiez le répertoire et tapez le nom de fichier.

3. Cliquez sur **Enregistrer.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Pour enregistrer un rapport de performances analysé à partir de la fenêtre d’affichage des rapports

1. Ouvrez les données de profilage (.*vsp*) dans la fenêtre d’affichage des rapports.

2. (Facultatif) Appliquez un filtre aux données. Pour plus d’informations, consultez filtre de la [vue rapport de performances](../profiling/performance-report-view-filter.md).

3. Cliquez sur **Enregistrer l’analyse** dans la barre d’outils de la fenêtre d’affichage des rapports.

4. Dans la boîte de dialogue **Enregistrer les données analysées** , spécifiez le répertoire et tapez le nom de fichier.

5. Cliquez sur **Enregistrer.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Comment exporter des rapports d’outils de profilage vers un fichier .xml ou .csv
 Vous pouvez exporter une ou plusieurs vues de rapport à partir d’un. fichier *vsp* ou. fichier de données de profilage *vsps* comme un fichier délimité par des virgules ou un fichier XML. Vous pouvez filtrer les données de la fenêtre d’affichage des rapports avant d’exporter, ou exporter des vues de rapport du fichier de données entier à partir de la fenêtre **Explorateur de performances** .

> [!NOTE]
> Vous pouvez également copier et coller des lignes sélectionnées à partir de la fenêtre d’affichage des rapports en tant que valeurs séparées par des tabulations.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Pour exporter des rapports de performances à partir de la fenêtre Explorateur de performances

1. Dans l’ **Explorateur de performances**, sélectionnez le rapport, cliquez avec le bouton droit et sélectionnez **Exporter**.

     La boîte de dialogue **Exporter le rapport** s’affiche.

2. Sélectionnez les vues de rapport à exporter.

3. Sous **Préfixer les rapports avec**, spécifiez le préfixe que vous souhaitez ajouter au nom du rapport.

4. Sous **Emplacement du rapport exporté**, spécifiez le répertoire.

5. Sous **Format du rapport exporté**, sélectionnez (délimité par des virgules) (\*.csv\) ou Données XML (\*.xml\).

6. Cliquez sur **Exporter**.

     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<prefix> _ \<report view name> .\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Pour exporter des rapports de performances à partir de la fenêtre d’affichage des rapports

1. Ouvrez le. fichier *vsp* dans la fenêtre d’affichage des rapports.

2. (Facultatif) Appliquez un filtre aux données. Pour plus d’informations, consultez filtre de la [vue rapport de performances](../profiling/performance-report-view-filter.md).

3. Cliquez sur **Exporter le rapport** dans la barre d’outils de la fenêtre d’affichage des rapports.

4. Sélectionnez les vues de rapport à exporter.

5. Sous **Préfixer les rapports avec**, spécifiez le préfixe que vous souhaitez ajouter au nom du rapport.

6. Sous **Emplacement du rapport exporté**, spécifiez le répertoire.

7. Sous **format du rapport exporté**, sélectionnez (délimité par des virgules) ( \* . csv) ou données XML ( \* . Xml).

8. Cliquez sur **Exporter**.

     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<prefix> _ \<report view name> .\<csv&#124;xml>

## <a name="see-also"></a>Voir aussi
- [Explorateur de performances](../profiling/performance-explorer.md)
- [Analyser les données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)
- [Comparer des fichiers de données de performances](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

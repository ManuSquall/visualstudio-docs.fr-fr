---
title: Enregistrement et exportation de données des outils d’analyse des performances | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 729dc2e28446420dd2590e132b7ec8a5444fcb9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773897"
---
# <a name="save-and-export-performance-tools-data"></a>Enregistrer et exporter les données des outils d’analyse des performances
Cet article décrit comment enregistrer et exporter des fichiers de données de performances.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Comment enregistrer des fichiers de données de performances en tant que fichiers de rapports analysés
 Vous pouvez enregistrer des vues filtrées ou non filtrées des données de profilage (.* vsp*) fichiers comme rapport analysé (.* vsps*) fichiers. Un fichier de rapport analysé peut être consulté dans la fenêtre de vue du rapport et est beaucoup plus petit que l’original . *fichier vsp.* Toutefois, vous ne pouvez pas appliquer un filtre aux données d’un . *fichier vsps.* Vous pouvez créer un fichier de rapport analysé à partir de l’Explorateur de performance sans ouvrir le fichier dans l’environnement de développement intégré (IDE), ou vous pouvez ouvrir et filtrer le . *vsp* fichier, puis enregistrer les résultats.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Pour enregistrer un rapport de performances analysé à partir de l’Explorateur de performances

1. Sous **rapports**, cliquez avec le bouton droit sur le fichier de données de profilage que vous souhaitez analyser, puis cliquez sur **Enregistrer l’analyse**.

2. Dans la boîte de dialogue **Enregistrer les données analysées** , spécifiez le répertoire et tapez le nom de fichier.

3. Cliquez **sur Enregistrer.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Pour enregistrer un rapport de performances analysé à partir de la fenêtre d’affichage des rapports

1. Ouvrez les données de profilage (.* vsp*) fichier dans la fenêtre de vue du rapport.

2. (Facultatif) Appliquez un filtre aux données. Pour plus d’informations, voir [Filtre de vue du rapport Performance](../profiling/performance-report-view-filter.md).

3. Cliquez sur **Enregistrer l’analyse** dans la barre d’outils de la fenêtre d’affichage des rapports.

4. Dans la boîte de dialogue **Enregistrer les données analysées** , spécifiez le répertoire et tapez le nom de fichier.

5. Cliquez **sur Enregistrer.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Comment exporter des rapports d’outils de profilage vers un fichier .xml ou .csv
 Vous pouvez exporter un ou plusieurs points de vue de rapport à partir d’un . *fichier vsp* ou un . *vsps* profilage fichier de données comme une virgule délimitée ou un fichier XML. Vous pouvez filtrer les données de la fenêtre d’affichage des rapports avant d’exporter, ou exporter des vues de rapport du fichier de données entier à partir de la fenêtre **Explorateur de performances** .

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

     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<préfixe>_\<nom_vue_rapport>.\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Pour exporter des rapports de performances à partir de la fenêtre d’affichage des rapports

1. Ouvrez le . fichier *vsp* dans la fenêtre de vue du rapport.

2. (Facultatif) Appliquez un filtre aux données. Pour plus d’informations, voir [Filtre de vue du rapport Performance](../profiling/performance-report-view-filter.md).

3. Cliquez sur **Exporter le rapport** dans la barre d’outils de la fenêtre d’affichage des rapports.

4. Sélectionnez les vues de rapport à exporter.

5. Sous **Préfixer les rapports avec**, spécifiez le préfixe que vous souhaitez ajouter au nom du rapport.

6. Sous **Emplacement du rapport exporté**, spécifiez le répertoire.

7. Sous **le format de rapport exporté**, sélectionnez (Comma délimité) (\*.csv), ou XML Data (\*.xml).

8. Cliquez sur **Exporter**.

     Chaque vue de rapport est enregistrée dans un fichier distinct nommé \<préfixe>_\<nom_vue_rapport>.\<csv&#124;xml>

## <a name="see-also"></a>Voir aussi
- [Explorateur de performances](../profiling/performance-explorer.md)
- [Analyser les données des outils de performance](../profiling/analyzing-performance-tools-data.md)
- [Comparer les fichiers de données de performance](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

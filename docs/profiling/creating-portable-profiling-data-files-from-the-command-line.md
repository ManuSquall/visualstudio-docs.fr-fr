---
title: Création de fichiers de données de profilage portables à partir de la ligne de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10f314f0b587c438c6691a6d7fe5d9d108d06479
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56654007"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Créer des fichiers de données de profilage portables à partir de la ligne de commande
Pour faciliter le partage des données de profilage, vous pouvez utiliser l’outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md) afin d’incorporer les symboles d’une exécution de profilage dans le fichier .*vsp*.

 Vous pouvez également créer un fichier de données de profilage préanalysé (.*vsps*), plus petit et donc plus rapide à charger dans l’IDE.

> [!NOTE]
>  Vérifiez que les fichiers de symboles (.*pdb*) sont accessibles à **VSPerfReport**. Pour plus d'informations, voir [Procédure : Spécifier les emplacements du fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
>  Pour plus d’informations sur le chemin de **VSReport**, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
>  Les données de profilage d’un fichier .*vsps* ne peuvent pas être filtrées.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Pour incorporer les symboles d’une exécution de profilage dans un fichier de données de profilage (.*vsp*)

- Dans une fenêtre d’invite de commandes, tapez la commande suivante :

   \<Chemin><strong>VSPerfReport \<</strong>Fichier VSP> **/PackSymbols**

   Par défaut, le fichier .*vsps* est nommé à partir du nom de base du fichier .*vsp*. Vous pouvez spécifier un autre nom avec l’option **Output**.

### <a name="to-create-a-summary-profiling-data-file"></a>Pour créer un fichier récapitulatif des données de profilage

- Dans une fenêtre d’invite de commandes, tapez la commande suivante :

   \<Chemin><strong>VSPerfReport \<</strong>Fichier VSP> **/SummaryFile** [**/Output:**\<Nom de fichier>]

   Par défaut, le fichier .*vsps* est nommé à partir du nom de base du fichier .*vsp*. Vous pouvez spécifier un autre nom avec l’option **Output**.
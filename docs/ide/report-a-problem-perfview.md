---
title: Collecter une trace ETL avec PerfView
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: ca2e44c41952a251d747f80fe27732c1d9dbd18b
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481952"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Collecter une trace ETL avec PerfView

PerfView est un outil qui crée des fichiers ETL (journal de suivi d’événements) en fonction du [suivi d’événements pour Windows](/windows/desktop/ETW/event-tracing-portal), qui peut être utile pour la résolution de certains types de problèmes avec Visual Studio. Il peut arriver que lorsque vous signalez un problème, l’équipe de produit peut vous demander d’exécuter PerfView pour collecter des informations supplémentaires.

## <a name="install-perfview"></a>Installer PerfView

Téléchargez PerfView à partir de [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Exécuter PerfView

1. Cliquez avec le bouton de droite sur **PerfView.exe** dans l’Explorateur Windows et choisissez **Exécuter en tant qu’administrateur** en tant qu’administrateur
1. Dans le menu Collecter, choisissez **Collecter**
1. Cochez **Zip**, **Fusion** et **ThreadTime**.
1. Augmenter **Mo circulaire** à 1000.
1. Modifiez **Rép actuel** pour enregistrer les traces ETL dans un dossier spécifié et le fichier de données si vous vous apprêtez à collecter plusieurs fois.
1. Pour démarrer l’enregistrement des données, choisissez le bouton **Démarrer la collecte**.
1. Pour arrêter l’enregistrement des données, choisissez le bouton **Arrêter la collecte**. Le fichier PrefView.etl.zip est enregistré dans le répertoire spécifié.

PerfView peut stocker uniquement les données les plus récentes qui s’adaptent à sa mémoire tampon. Par conséquent, essayez d’arrêter la collecte dès que possible après le démarrage de Visual Studio pour la geler ou la ralentir. Ne collectez pas pendant plus de 30 secondes une fois le problème atteint.

Pour plus d’informations, consultez [Didacticiel PerfView sur Channel9](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).

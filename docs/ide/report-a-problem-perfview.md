---
title: Collecter une trace ETL avec PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 9ac4d90a0da15fe2415ada02d6e8e1cdbe11af56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770816"
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

Pour plus d’informations, consultez [Didacticiel PerfView sur Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).

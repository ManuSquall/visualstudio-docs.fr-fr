---
title: Collecter une trace ETL avec PerfView
ms.date: 06/27/2019
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
ms.openlocfilehash: 6b1f61888fa642ed544c6da7d1cf77c43b52b2d9
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461551"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Collecter une trace ETL avec PerfView

PerfView est un outil qui crée des fichiers ETL (journal de suivi d’événements) en fonction du [suivi d’événements pour Windows](/windows/desktop/ETW/event-tracing-portal), qui peut être utile pour la résolution de certains types de problèmes avec Visual Studio. Il peut arriver que lorsque vous signalez un problème, l’équipe de produit peut vous demander d’exécuter PerfView pour collecter des informations supplémentaires.

## <a name="install-perfview"></a>Installer PerfView

Téléchargez PerfView à partir du [Centre de téléchargement Microsoft](http://www.microsoft.com/download/details.aspx?id=28567).

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

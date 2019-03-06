---
title: Dépannage des outils d’analyse des performances | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68250d8767910106ab7e6a3c3239beeb292bdfd8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620809"
---
# <a name="troubleshoot-performance-tools-issues"></a>Résoudre les problèmes liés aux outils d’analyse des performances
Vous pouvez rencontrer les problèmes suivants quand vous utilisez les outils de profilage :

-   [Aucune donnée n’est collectée par les outils de profilage](#no-data-is-collected-by-the-profiling-tools)

-   [Les vues et les rapports de performances affichent des numéros pour les noms des fonctions](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Aucune donnée n’est collectée par les outils de profilage
 Une fois l’application profilée, aucun fichier de données de profilage (.*vsp*) n’est créé, et l’avertissement suivant s’affiche dans la fenêtre **Sortie** ou la fenêtre Commande :

 PRF0025 : Aucune donnée n’a été collectée.

 Ce problème peut avoir plusieurs causes :

-   Un processus qui a été profilé à l’aide de l’échantillonnage ou de la méthode de mémoire .NET démarre un processus enfant qui devient le processus effectuant le travail de l’application. Par exemple, certaines applications lisent la ligne de commande pour déterminer si elles ont été démarrées comme application Windows ou comme application de ligne de commande. Si une application Windows a été demandée, le processus d’origine démarre un nouveau processus configuré comme application Windows et le processus d’origine se ferme alors. Comme les outils de profilage ne collectent pas automatiquement les données pour les processus enfants, aucune donnée n’est collectée.

     Pour collecter des données de profilage dans ce cas, attachez le profileur au processus enfant au lieu de démarrer l’application avec le profileur. Pour plus d'informations, voir [Procédure : Attacher les outils d’analyse des performances à des processus en cours d’exécution ou les en détacher](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) et [Attach (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Les vues et les rapports de performances affichent des numéros pour les noms des fonctions
 Après avoir profilé une application, vous voyez des numéros au lieu des noms des fonctions dans les rapports et les vues.

 Ce problème est dû au fait que le moteur d’analyse des Outils de profilage ne peut pas trouver les fichiers .*pdb* contenant les informations de symbole qui mappent les informations du code source, par exemple les noms de fonctions et les numéros de lignes, au fichier compilé. Par défaut, le compilateur crée le fichier *.pdb* durant la génération du fichier d’application. Une référence au répertoire local du fichier .*pdb* est stockée dans l’application compilée. Le moteur d’analyse recherche le fichier .*pdb* dans le répertoire référencé, puis dans le fichier qui contient le fichier d’application. Si le fichier .*pdb* est introuvable, le moteur d’analyse utilise les décalages de fonctions au lieu des noms de fonctions.

 Vous pouvez résoudre le problème de deux manières :

-   Recherchez les fichiers .*pdb* et placez-les dans le même répertoire que les fichiers d’application.

-   Incorporez les informations de symboles dans le fichier de données de profilage (.*vsp*). Pour plus d’informations, consultez [Enregistrer les informations de symbole avec des fichiers de données de performances](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
>  Le moteur d’analyse nécessite un fichier .*pdb* ayant la même version que le fichier d’application compilé. Un fichier .*pdb* provenant d’une build antérieure ou ultérieure du fichier d’application ne fonctionnera pas.
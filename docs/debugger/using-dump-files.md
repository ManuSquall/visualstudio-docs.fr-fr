---
title: Utiliser des fichiers de vidage dans le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0adb7e86f2b14dd25fa333fe54cc5121bbc8c1f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012493"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Fichiers de vidage dans le débogueur Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> Un *fichier dump* est un instantané qui affiche les processus qui s’exécutait et les modules qui ont été chargées pour une application à un point dans le temps. À ce stade, un vidage avec les informations du tas inclut également un instantané de la mémoire de l’application. 

L’ouverture d’un fichier dump avec un segment de mémoire dans Visual Studio est similaire à l’arrêt à un point d’arrêt dans une session de débogage. Bien que vous ne pouvez pas poursuivre l’exécution, vous pouvez examiner les piles, les threads et les valeurs des variables de l’application au moment de l’image mémoire.

Dumps sont principalement utilisées pour déboguer les problèmes à partir d’ordinateurs que les développeurs n’ont pas accès. Vous pouvez utiliser un fichier de vidage à partir de l’ordinateur d’un client lorsque vous ne pouvez pas reproduire un blocage ou se bloque sur votre propre ordinateur. Les testeurs créent également des vidages pour enregistrer l’incident ou de données à utiliser pour tester plus de blocage. 

Le débogueur Visual Studio peut enregistrer des fichiers dump pour le code managé ou natif. Il puisse déboguer des fichiers dump créés par Visual Studio ou par d’autres applications qui enregistrent les fichiers dans le *minidump* format.

##  <a name="BKMK_Requirements_and_limitations"></a> Configuration requise et limitations

-   Pour déboguer les fichiers de vidage à partir des ordinateurs 64 bits, Visual Studio doit s’exécuter sur un ordinateur 64 bits.

-   Visual Studio peut déboguer les fichiers dump des applications natives à partir des périphériques ARM. Il peut également déboguer des fichiers dump des applications gérées à partir d’appareils ARM, mais uniquement dans le débogueur natif.

-   Pour déboguer [en mode noyau](/windows-hardware/drivers/debugger/kernel-mode-dump-files) fichiers dump ou utiliser le [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) débogage extension dans Visual Studio, téléchargez les outils de débogage pour Windows dans le [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio ne peut pas déboguer des fichiers dump enregistrés dans l’ancien [dump complet en mode utilisateur](/windows/desktop/wer/collecting-user-mode-dumps) format. Un vidage complet en mode utilisateur n’est pas un dump avec tas.

-   Le débogage des fichiers dump de code optimisé peut faire l'objet de confusion. Par exemple, l’incorporation du compilateur des fonctions peut entraîner des piles d’appels inattendues et d’autres optimisations peuvent modifier la durée de vie des variables.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Fichiers dump, avec ou sans tas

Fichiers de vidage peuvent ou peut-être pas les informations de segment de mémoire.

-   **Fichiers dump avec tas** contiennent un instantané de la mémoire de l’application, y compris les valeurs des variables, au moment de l’image mémoire. Visual Studio enregistre également les fichiers binaires des modules natifs chargés dans un fichier dump avec un segment de mémoire, ce qui peut faciliter le débogage. Visual Studio peut charger les symboles à partir d’un fichier dump avec un segment de mémoire, même si elle ne peut pas trouver une application binaire. 

-   **Fichiers dump sans tas** sont beaucoup plus petits que les dumps avec tas, mais le débogueur doit charger les binaires d’application pour rechercher des informations de symboles. Les fichiers binaires chargés doivent correspondre exactement à ceux en cours d’exécution lors de la création du dump. Fichiers dump sans tas enregistrez les valeurs des variables de pile uniquement.

##  <a name="BKMK_Create_a_dump_file"></a> Créer un fichier dump

Lorsque vous déboguez un processus dans Visual Studio, vous pouvez enregistrer un fichier de vidage lorsque le débogueur s’est arrêté sur une exception ou un point d’arrêt. 

Avec [débogage juste à temps](../debugger/just-in-time-debugging-in-visual-studio.md) activé, vous pouvez attacher le débogueur de Visual Studio à un processus bloqué en dehors de Visual Studio, puis enregistrez un fichier de vidage à partir du débogueur. Consultez [attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Pour enregistrer un fichier dump :**

1. Lorsque vous êtes à une erreur ou un point d’arrêt pendant le débogage, sélectionnez **déboguer** > **enregistrer le Dump sous**. 

1. Dans le **enregistrer le Dump sous** boîte de dialogue **enregistrer en tant que type**, sélectionnez **Minidump** ou **Minidump avec segment mémoire** (la valeur par défaut).

1. Accédez à un chemin d’accès et sélectionnez un nom pour le fichier de vidage, puis **enregistrer**. 

>[!NOTE]
>Vous pouvez créer des fichiers dump avec n’importe quel programme prenant en charge le format minidump Windows. Par exemple, l’utilitaire en ligne de commande **Procdump** de [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) peut créer des fichiers de processus de vidage sur incident sur des déclencheurs ou à la demande. Consultez [spécifications et limitations](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) pour plus d’informations sur l’utilisation d’autres outils pour créer des fichiers de vidage.

##  <a name="BKMK_Open_a_dump_file"></a> Ouvrir un fichier dump

1. Dans Visual Studio, sélectionnez **fichier** > **Open** > **fichier**.

1. Dans la boîte de dialogue **Ouvrir un fichier**, localisez et sélectionnez le fichier dump. Il porte généralement une extension *.dmp*. Sélectionnez **OK**.

   Le **résumé du fichier Minidump** fenêtre affiche les informations résumé et le module pour le fichier de vidage et les actions que vous pouvez prendre.

   ![Page de résumé minidump](../debugger/media/dbg_dump_summarypage.png "page de résumé Minidump")

1. Sous **Actions**:
   - Pour définir le symbole du chargement des emplacements, sélectionnez **définir les chemins de symboles**.
   - Pour démarrer le débogage, sélectionnez **déboguer avec managé uniquement**, **déboguer avec natif uniquement**, **déboguer avec mixte**, ou **déboguer avec la mémoire managée**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Rechercher des fichiers .exe, .pdb et source

Pour utiliser complet de fonctionnalités sur un fichier de vidage de débogage Visual Studio a besoin :

- Le *.exe* le dump a été créé pour des fichiers et autres fichiers binaires (DLL, etc.) que le processus de vidage utilisé.
- Fichiers de symboles (*.pdb*) pour le fichier *.exe* et d’autres fichiers binaires.
- Le *.exe* et *.pdb* vider les fichiers qui correspondent exactement à la version et la génération des fichiers à la création.
- Fichiers sources pour les modules appropriés. Vous pouvez utiliser le code machine des modules si vous ne trouvez pas les fichiers sources.

Si le vidage a des données de tas, Visual Studio peut gérer les binaires manquants de certains modules, mais il doit avoir des binaires pour suffisamment de modules générer des piles d’appels valides. 

### <a name="search-paths-for-exe-files"></a>Chemins de recherche pour les fichiers .exe

Visual Studio recherche automatiquement ces emplacements pour *.exe* fichiers qui ne sont pas inclus dans le fichier de vidage :

1. Le dossier qui contient le fichier de vidage.
2. Le chemin d’accès du module du fichier de vidage Spécifie, qui est le chemin d’accès du module sur l’ordinateur qui collectées le vidage.
3. Les chemins d’accès aux symboles spécifiés dans **outils** (ou **déboguer**) > **Options** > **débogage**  >  **Symboles**. Vous pouvez également ouvrir le **symboles** page à partir de la **Actions** volet de la **résumé du fichier minidump** fenêtre. Dans cette page, vous pouvez ajouter d’autres emplacements à rechercher.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Utilisez les pages non binaire, aucun symbole ou aucune Source trouvée

Si Visual Studio ne peut pas trouver les fichiers qu’il a besoin déboguer un module dans le fichier de vidage, il affiche un **aucun binaire trouvé**, **aucun symbole trouvé**, ou **aucune Source trouvée** page. Ces pages fournissent des informations détaillées sur la cause du problème et fournissent des liens d’action qui peuvent vous aider à localiser les fichiers. Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Voir aussi

- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)
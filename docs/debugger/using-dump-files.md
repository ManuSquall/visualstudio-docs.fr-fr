---
title: Utiliser des fichiers Dump | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 03/08/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d46bbe3eb392de21cc1b165819fe469eb4de726d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755883"
---
# <a name="use-dump-files-with-visual-studio"></a>Utiliser des fichiers Dump avec Visual Studio
Fichiers dump avec ou sans tas ; créer un fichier dump ; ouvrir un fichier dump ; Recherchez les fichiers binaires, du fichier pdb et fichier source pour un fichier de vidage.

##  <a name="BKMK_What_is_a_dump_file_"></a> Qu’est un fichier dump ?
 Un *fichier dump* est un instantané d’une application au point dans le temps le dump a été pris. Il indique quel processus s'exécutait et quels modules ont été chargés. Si le dump a été stocké avec les informations du tas, le fichier dump contiendra un instantané de ce qui était dans la mémoire de l'application à ce moment. L'ouverture d'un fichier dump avec un tas dans Visual Studio est semblable à l'arrêt à un point d'arrêt dans la session de débogage. Bien que vous ne puissiez pas continuer l'exécution, vous pouvez examiner les piles, les threads, et les valeurs de variables de l'application au moment où le dump s'est produit.

 Dumps sont principalement utilisées pour résoudre les problèmes qui se produisent sur les ordinateurs qui le développeur n’a pas accès. Par exemple, vous pouvez utiliser un fichier de vidage à partir de l’ordinateur d’un client lorsque vous ne pouvez pas reproduire sur incident du client ou de blocage sur votre ordinateur. Les dumps sont également créés par les testeurs pour enregistrer les données d'incident et pour que l'ordinateur de test puisse effectuer plus de tests. Le débogueur Visual Studio peut enregistrer des fichiers dump pour le code managé ou natif. Le débogueur peut charger des fichiers dump créés par Visual Studio ou par d’autres programmes qui enregistrent les fichiers dans le *minidump* format.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Fichiers dump, avec ou sans tas
 Vous pouvez créer des fichiers dump avec ou sans information du tas.

-   **Fichiers dump avec tas** contiennent un instantané de la mémoire de l’application. Cela inclut les valeurs de variables lorsque le dump a été créé. Si vous chargez un fichier dump qui été enregistré avec un tas, Visual Studio peut charger les symboles même si l'application binaire est introuvable. Visual Studio enregistre également les binaires des modules natifs chargés dans le fichier dump, ce qui peut faciliter le débogage.

-   **Fichiers dump sans tas** sont beaucoup plus petite que les vidages sur incident avec les informations du tas. Toutefois, le débogueur doit charger les binaires d'application pour trouver les informations de symbole. Les binaires doivent être une correspondance exacte des binaires utilisés lors de la création du dump. Seules les valeurs des variables de pile sont stockées dans des fichiers dump sans données de tas.

##  <a name="BKMK_Requirements_and_limitations"></a> Configuration requise et limitations

-   Le débogage des fichiers dump de code optimisé peut faire l'objet de confusion. Par exemple, l'incorporation du compilateur des fonctions peut entraîner des piles d'appels inattendues et d'autres optimisations peuvent modifier la durée de vie des variables.

-   Les fichiers dump des ordinateurs 64 bits doivent être débogués sur une instance de Visual Studio qui s'exécute sur un ordinateur 64 bits.

-   Dans les versions de Visual Studio antérieures à VS 2013, les fichiers dump des applications 32 bits exécutées sur des ordinateurs 64 bits, qui étaient collectés par certains outils (tels que le Gestionnaire des tâches et WinDbg 64 bits), ne pouvaient pas être ouverts dans Visual Studio. Cette limitation a été supprimée dans VS 2013.

-   Visual Studio peut déboguer les fichiers dump des applications natives à partir des périphériques ARM. Visual Studio peut également déboguer les fichiers dump des applications managées à partir des périphériques ARM, mais uniquement dans le débogueur natif.

-   Pour déboguer [en mode noyau](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) fichiers dump, téléchargez les outils de débogage pour Windows qui fait partie de la [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio ne peut pas déboguer des fichiers dump enregistrés dans l’ancien format dump appelé un [dump complet en mode utilisateur](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Notez qu'un dump complet en mode utilisateur n'est pas le même qu'un dump avec le tas.

-   Pour déboguer avec le [SOS.dll (Extension de débogage SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension) dans Visual Studio, vous devez installer les outils de débogage pour Windows qui fait partie de la [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk)

##  <a name="BKMK_Create_a_dump_file"></a> Créer un fichier dump
 Pour créer un fichier dump avec Visual Studio :

-   Lorsque vous déboguez un processus dans Visual Studio, vous pouvez enregistrer un fichier dump lorsque le débogueur s'est arrêté à une exception ou à un point d'arrêt. Choisissez **déboguer**, puis **enregistrer le Dump sous**, puis **déboguer**. Dans le **enregistrer le Dump sous** boîte de dialogue le **enregistrer en tant que type** liste, vous pouvez sélectionner **Minidump** ou **Minidump avec segment mémoire** (la valeur par défaut).

-   Avec [débogage juste à temps](../debugger/just-in-time-debugging-in-visual-studio.md) activé, vous pouvez attacher le débogueur à un processus bloqué qui s’exécute en dehors du débogueur, puis enregistrez un fichier de vidage. Consultez [attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

 Vous pouvez également créer des fichiers dump avec n'importe quel programme qui prend en charge le format minidump Windows. Par exemple, le **Procdump** utilitaire de ligne de commande à partir de [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) peut créer des fichiers de vidage sur incident de processus basés sur des déclencheurs ou à la demande. Consultez [spécifications et limitations](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) dans cette rubrique pour plus d’informations sur l’utilisation d’autres outils pour créer des fichiers de vidage.

##  <a name="BKMK_Open_a_dump_file"></a> Ouvrir un fichier dump

1.  Dans Visual Studio, choisissez **fichier**, **Open**, **fichier**.

2.  Dans le **ouvrir un fichier** boîte de dialogue, recherchez et sélectionnez le fichier de vidage. Il porte généralement une extension .dmp. Puis choisissez **OK**.

3.  Le **résumé du fichier minidump** fenêtre s’affiche. Dans cette fenêtre, vous pouvez afficher les informations de résumé de débogage du fichier dump, définir le chemin d’accès aux symboles, commencer le débogage et copier les informations de résumé vers le Presse-papiers.

     ![Page de résumé minidump](../debugger/media/dbg_dump_summarypage.png "DBG_DUMP_SummaryPage")

4.  Pour démarrer le débogage, accédez à la **Actions** section et choisissez **déboguer avec managé uniquement**, **déboguer avec natif uniquement** ou **déboguer avec mixte**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Rechercher les binaires, les fichiers de symboles (.pdb) et les fichiers sources
 Pour utiliser les fonctionnalités complètes de Visual Studio pour déboguer un fichier dump, vous devez accéder à :

-   Fichier .exe pour lequel le dump a été effectué et autres fichiers binaires (DLL, etc.) utilisés dans le processus de dump.

     Si vous déboguez un dump avec des données de tas, Visual Studio peut gérer les binaires manquantes pour certains modules, mais doit avoir des binaires pour que suffisamment de modules génèrent des piles d'appels valides. Visual Studio inclut les modules natifs dans un fichier dump avec tas.

-   Fichiers de symboles (.pdb) pour le fichier .exe et autres fichiers binaires.

-   Fichiers sources des modules qui vous intéressent.

     Les fichiers exécutables et .pdb doivent correspondre exactement à la version et à la build des fichiers utilisés lors de la création du dump.

     Vous pouvez déboguer à l’aide du code machine des modules si vous ne trouvez pas les fichiers source,

 **Chemins de recherche par défaut pour les fichiers exécutables**

 Visual Studio recherche automatiquement ces emplacements pour les fichiers exécutables qui ne sont pas inclus dans le fichier dump :

1.  Répertoire qui contient le fichier dump.

2.  Chemin d’accès du module spécifié dans le fichier dump. Il s’agit du chemin d’accès du module sur l’ordinateur où le dump a été collecté.

3.  Les chemins d’accès aux symboles spécifiés dans le **débogage**, **Options**, **symboles** page de Visual Studio **outils**, **Options**  boîte de dialogue. Vous pouvez ajouter d'autres emplacements à rechercher sur cette page.

 **À l’aide de la non binaire > Symbole > Source de pages**

 Si Visual Studio ne peut pas trouver les fichiers nécessaires pour déboguer un module dans le fichier de vidage, il affiche une page appropriée (**aucun binaire trouvé**, **aucun symbole trouvé**, ou **aucune Source trouvée**). Ces pages fournissent des informations détaillées sur la cause du problème et fournissent des liens d'action qui peuvent vous aider à identifier l'emplacement correct des fichiers. Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Voir aussi

- [le débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)
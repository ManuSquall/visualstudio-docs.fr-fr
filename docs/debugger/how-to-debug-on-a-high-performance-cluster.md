---
title: Déboguer sur un cluster High-Performance | Microsoft Docs
description: Découvrez ce qui est particulier pour déboguer un programme multitraitement sur un cluster hautement performant. Deux fenêtres sont particulièrement utiles et il existe des techniques spéciales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b19f1d919095f30e4408056e49847c3c9ba5671
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903105"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Comment : déboguer sur un cluster High-Performance (C#, Visual Basic, C++)

Le débogage d'un programme multitraitement sur un cluster hautement performant est identique au débogage d'un programme ordinaire sur un ordinateur distant. Il y a toutefois d'autres éléments à prendre en compte. Pour connaître la configuration générale requise pour l’installation à distance, consultez [débogage à distance](../debugger/remote-debugging.md).

 Lorsque vous déboguez sur un cluster hautement performant, vous pouvez utiliser toutes les fenêtres de débogage et les techniques [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disponibles pour le débogage distant. Cependant, puisque vous déboguez à distance, la fenêtre de console externe n'est pas disponible.

 Les fenêtres **Threads** et **Processus** sont particulièrement utiles pour déboguer des applications parallèles. Pour obtenir des conseils sur l’utilisation de ces fenêtres, consultez [Comment : Utiliser la fenêtre processus](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) et [procédure pas à pas : Déboguer à l’aide de la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).

 Les procédures suivantes présentent quelques techniques particulièrement utiles pour le débogage sur un cluster hautement performant.

 Lors du débogage d'une application parallèle, vous souhaitez définir un point d'arrêt sur un thread, un processus ou un ordinateur particulier. Pour ce faire, vous pouvez créer un point d'arrêt normal, puis ajouter un filtre de point d'arrêt.

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Pour ouvrir la boîte de dialogue Filtre de point d'arrêt

1. Cliquez avec le bouton droit sur un glyphe de point d’arrêt dans une fenêtre source, la fenêtre **Code machine**, **Pile des appels** ou **Points d’arrêt**.

2. Dans le menu contextuel, cliquez sur **Filtre**. Cette option peut s’afficher en haut ou dans le sous-menu sous **Points d’arrêt**.

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Pour définir un point d'arrêt sur un ordinateur spécifique

1. Obtenez le nom de l’ordinateur dans la fenêtre **Processus**.

2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la procédure précédente.

3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :

     MachineName =*nom_de_votre_ordinateur*

     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.

4. Cliquez sur **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Pour définir un point d'arrêt sur un processus spécifique

1. Obtenez le nom du processus ou le numéro d’identifiant du processus de la fenêtre **Processus**.

2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la première procédure.

3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :

     `ProcessName =`  *nom_de_votre_processeur*

     Ou

     `ProcessID =` *ID_de_votre_processeur*

     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.

4. Cliquez sur **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Pour définir un point d'arrêt sur un thread spécifique

1. Obtenez le nom du thread ou le numéro d’ID de thread dans la fenêtre **Threads**.

2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la première procédure.

3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :

     `ThreadName =` *nom_de_votre_thread*

     Ou

     `ThreadID =` *ID_de_votre_thread*

     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.

4. Cliquez sur **OK**.

## <a name="example"></a> Exemple
 L'exemple suivant montre comment créer un filtre pour un point d'arrêt sur un ordinateur nommé `marvin` et un thread nommé `fourier1`.

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Débogage à distance](../debugger/remote-debugging.md)
- [Comment : utiliser la fenêtre processus](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Prise en main du débogage des applications multithread](../debugger/get-started-debugging-multithreaded-apps.md)
- [Threads et processus](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)
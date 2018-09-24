---
title: Guide pratique pour limiter l’instrumentation à des DLL spécifiques | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aefa0d5953d1e8d61615ac5bfe0af136082c96f3
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843947"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Guide pratique pour limiter l’instrumentation à des DLL spécifiques

La méthode de profilage par instrumentation vous permet de limiter la collecte de données de profilage à une ou plusieurs DLL d’une application. Pour profiler une ou plusieurs DLL d’une application, créez une session de performance qui comprend les fichiers .*dll* comme cibles. Vous pouvez spécifier les DLL à profiler en tant que projets dans une solution Visual Studio, ou en tant que fichiers binaires indépendants.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Pour limiter l’instrumentation à certaines DLL dans une solution Visual Studio

1. Ouvrez la solution qui contient la DLL dans Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Lancer l’Assistant Performance**.

3. Choisissez **Instrumentation** comme méthode de profilage, puis cliquez sur **Suivant**.

4. Dans la page **Laquelle des cibles disponibles suivantes voulez-vous profiler ?**, sélectionnez le nom du projet .*dll*, puis cliquez sur **Suivant**.

5. Cliquez sur **Terminer** pour quitter l’Assistant et afficher la nouvelle session de performance dans l’**Explorateur de performances**.

6. Cliquez avec le bouton droit sur **Cibles**, puis sélectionnez **Ajouter un projet cible**.

7. Dans la liste **Ajouter un projet cible**, sélectionnez le projet exécutable que vous voulez utiliser pour la DLL.

     Facultative. Vous pouvez ajouter autant de projets de DLL que vous le voulez pour le profilage.

8. Pour empêcher la collecte de données pour un projet ajouté, cliquez sur le nom du projet, puis décochez la case **Instrumenter**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Pour spécifier des DLL à profiler en tant que fichiers binaires indépendants

1. Ouvrez Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Lancer l’Assistant Performance**.

3. Dans la page **Laquelle des cibles disponibles suivantes voulez-vous profiler ?**, sélectionnez l’option **Profiler une bibliothèque de liens dynamiques**, puis cliquez sur **Suivant**.

4. Dans la deuxième page de l’Assistant, effectuez les étapes suivantes :

    - Tapez le chemin et le nom du fichier .*dll* à profiler dans **Chemin d’accès de la DLL**. Vous pouvez également cliquer sur le bouton de sélection (...) pour rechercher le fichier dans la boîte de dialogue **Bibliothèque de liens dynamiques à profiler**. Notez que vous devez spécifier la copie du fichier .*dll* qui sera lancé par le fichier exécutable (.*exe*) que vous allez sélectionner.

    - Tapez le chemin et le nom du fichier exécutable (.*exe*) qui doit exécuter le fichier .*dll* dans **Chemin d’accès de l’exécutable**. Vous pouvez également cliquer sur le bouton de sélection (...) pour rechercher le fichier dans la boîte de dialogue **Exécutable à lancer**.

    - Facultative. Dans **Arguments de ligne de commande**, tapez les arguments de ligne de commande que vous voulez passer au fichier exécutable. Si nécessaire, spécifiez le répertoire de travail de l’application dans **Répertoire de travail**.

    - Cliquez sur **Suivant**.

5. Choisissez **Instrumentation** comme méthode de profilage, puis cliquez sur **Suivant**.

6. Cliquez sur **Terminer** pour quitter l’Assistant et afficher la nouvelle session de performance dans l’**Explorateur de performances**.

7. Facultative. Pour ajouter des fichiers .*dll*, cliquez avec le bouton droit sur **Cibles**, puis sélectionnez **Ajouter un fichier binaire cible**. Sélectionnez les fichiers dans la boîte de dialogue **Ajouter un fichier binaire cible**.

    > [!NOTE]
    > Ne spécifiez pas le fichier exécutable (.*exe*) qui exécute les DLL.

## <a name="see-also"></a>Voir aussi

[Contrôler la collecte des données](../profiling/controlling-data-collection.md)  
[Guide pratique pour limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
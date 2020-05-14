---
title: Guide pratique pour limiter l’instrumentation à des DLL spécifiques | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778815"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Guide pratique pour limiter l’instrumentation à des DLL spécifiques

La méthode de profilage par instrumentation vous permet de limiter la collecte de données de profilage à une ou plusieurs DLL d’une application. Pour profiler un ou plusieurs DLL dans une application, vous créez une session de performance qui inclut le . *dll* fichiers comme cibles. Vous pouvez spécifier les DLL à profiler en tant que projets dans une solution Visual Studio, ou en tant que fichiers binaires indépendants.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Pour limiter l’instrumentation à certaines DLL dans une solution Visual Studio

1. Ouvrez la solution qui contient la DLL dans Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Lancer l’Assistant Performance**.

3. Choisissez **Instrumentation** comme méthode de profilage, puis cliquez sur **Suivant**.

4. Parmi les **cibles disponibles suivantes, souhaitez-vous profiler ?**, sélectionnez le nom de la . *dll* projet, puis cliquez sur **Next**.

5. Cliquez sur **Terminer** pour quitter l’Assistant et afficher la nouvelle session de performance dans l’**Explorateur de performances**.

6. Cliquez avec le bouton droit sur **Cibles**, puis sélectionnez **Ajouter un projet cible**.

7. Dans la liste **Ajouter un projet cible**, sélectionnez le projet exécutable que vous voulez utiliser pour la DLL.

     facultatif. Vous pouvez ajouter autant de projets de DLL que vous le voulez pour le profilage.

8. Pour empêcher la collecte de données pour un projet ajouté, cliquez sur le nom du projet, puis décochez la case **Instrumenter**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Pour spécifier des DLL à profiler en tant que fichiers binaires indépendants

1. Ouvrez Visual Studio.

2. Dans le menu **Analyser**, sélectionnez **Lancer l’Assistant Performance**.

3. Dans la page **Laquelle des cibles disponibles suivantes voulez-vous profiler ?**, sélectionnez l’option **Profiler une bibliothèque de liens dynamiques**, puis cliquez sur **Suivant**.

4. Dans la deuxième page de l’Assistant, effectuez les étapes suivantes :

    - Tapez le chemin et le nom de fichier de la . *fichier dll* que vous voulez profiler dans **le chemin Dll**. Vous pouvez également cliquer sur le bouton de sélection (...) pour rechercher le fichier dans la boîte de dialogue **Bibliothèque de liens dynamiques à profiler**. Notez que vous devez spécifier la copie de la . *dll* fichier qui sera lancé par l’exécutable (.* exe*) fichier que vous sélectionnez ensuite.

    - Tapez le chemin et le nom du fichier de l’exécutable (.* exe*) fichier qui exercera le . *dll* dans **le chemin Exécutable**. Vous pouvez également cliquer sur le bouton de sélection (...) pour rechercher le fichier dans la boîte de dialogue **Exécutable à lancer**.

    - facultatif. Dans **Arguments de ligne de commande**, tapez les arguments de ligne de commande que vous voulez passer au fichier exécutable. Si nécessaire, spécifiez le répertoire de travail de l’application dans **Répertoire de travail**.

    - Cliquez sur **Suivant**.

5. Choisissez **Instrumentation** comme méthode de profilage, puis cliquez sur **Suivant**.

6. Cliquez sur **Terminer** pour quitter l’Assistant et afficher la nouvelle session de performance dans l’**Explorateur de performances**.

7. facultatif. Pour en ajouter d’autres . *fichiers dll,* clic droit **Cibles,** puis sélectionnez **Ajouter Target Binaire**. Sélectionnez les fichiers dans la boîte de dialogue **Ajouter un fichier binaire cible**.

    > [!NOTE]
    > Ne spécifiez pas l’exécutable (.* exe*) fichier qui exerce les DLL.

## <a name="see-also"></a>Voir aussi

[Contrôlez la collecte de](../profiling/controlling-data-collection.md)
données[Comment : Limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)

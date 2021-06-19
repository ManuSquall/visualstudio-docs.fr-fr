---
title: Préparer le débogage de projets C++ | Microsoft Docs
description: Obtenir des informations sur la préparation du débogage des types de projet de base créés par les modèles de projet Visual C++ dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 258671ca0426cb877d7cdf4bfc0b0f8f6095253c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387838"
---
# <a name="debugging-preparation-c-project-types"></a>Préparation du débogage : types de projets C++
Cette section explique le débogage de types de projets de base, créés par les modèles de projet [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].

 Notez que les types de projet qui créent des dll en tant que sortie ont été regroupés en [projets de dll de débogage](../debugger/debugging-dll-projects.md) en raison des fonctionnalités communes qu’ils partagent.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique
 [Paramètres de propriété recommandés](#BKMK_Recommended_Property_Settings)

 [Projets Win32](#BKMK_Win32_Projects)

- [Pour déboguer une application Win32 C ou C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Pour définir manuellement une configuration Debug](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Paramètres de propriété recommandés
 Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage non managé. Les tableaux suivants présentent les paramètres de propriété recommandés. Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet non managés. Pour plus d’informations, consultez [paramètres de projet pour une configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propriétés de configuration &#124; nœud d’optimisation du &#124; C/C++

|Nom de la propriété|Paramètre|
|-------------------|-------------|
|**Optimisation**|Affectez la valeur **Désactivé (/0d).** Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous trouvez que votre programme présente un bogue uniquement dans du code optimisé, vous pouvez activer ce paramètre, tout en gardant à l’esprit que le code affiché dans la fenêtre **Code machine** est généré à partir d’une source optimisée qui peut ne pas correspondre à ce que vous voyez dans vos fenêtres sources. D'autres fonctionnalités, telles que l'exécution pas à pas, peuvent ne pas se comporter comme prévu.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propriétés de configuration &#124; éditeur de liens &#124; le nœud de débogage

|Nom de la propriété|Paramètre|
|-------------------|-------------|
|**Générer des informations de débogage**|Vous devez toujours définir cette option sur **Oui (/DEBUG)** pour créer les symboles et fichiers nécessaires au débogage. Lorsque l'application passe en phase de production, vous pouvez la désactiver.|

 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Projets Win32
 Les applications Windows32 sont des programmes Windows traditionnels écrits en C ou C++. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple.

 Les applications Win32 comprennent les applications MFC et les projets ATL. Elles utilisent les API Windows et parfois également MFC ou ATL, mais elles n'utilisent pas le Common Language Runtime (CLR). Toutefois, elles peuvent appeler du code managé qui utilise le CLR.

 La procédure suivante explique comment déboguer un projet Win32 à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Une autre façon de déboguer une application Win32 consiste à démarrer l'application en dehors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puis de l'attacher. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Pour déboguer une application Win32 C ou C++

1. Ouvrez le projet dans Visual Studio.

2. Dans le menu **Déboguer**, choisissez **Démarrer**.

3. Déboguez à l’aide des techniques abordées dans [premier aperçu du débogueur](../debugger/debugger-feature-tour.md).

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Pour définir manuellement une configuration Debug

1. Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.

2. Cliquez sur le nœud **Propriétés de configuration** pour l’ouvrir s’il ne l’est pas déjà

3. Sélectionnez **Général** et affectez la valeur **Debug** à la ligne **Sortie**.

4. Ouvrez le nœud **C/C++** et sélectionnez **Général**.

    À la ligne **Déboguer**, spécifiez le type d’informations de débogage que le compilateur doit générer. Vous pouvez notamment choisir **Base de données du programme (/Zi)** ou **Base de données du programme pour Modifier & Continuer**.

5. Sélectionnez **Optimisation** puis, dans la ligne **Optimisation**, sélectionnez **Désactivé (/0d)** dans la liste déroulante.

    Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous constatez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais rappelez-vous que le code affiché dans la fenêtre Code Machine est généré à partir d'une source optimisée qui ne correspond peut-être pas à ce que vous voyez dans vos fenêtres sources. Certains fonctionnalités, telles que l'exécution pas à pas, peuvent afficher des points d'arrêt et un point d'exécution incorrects.

6. Ouvrez le nœud **Éditeur de liens** et sélectionnez **Débogage**. Dans la première ligne **Générer**, sélectionnez **Oui (/DEBUG)** dans la liste déroulante. Sélectionnez toujours ce paramètre lorsque vous déboguez.

   Pour plus d’informations, consultez[paramètres de projet pour une configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Voir aussi
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Attachement à un ou plusieurs programmes en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)
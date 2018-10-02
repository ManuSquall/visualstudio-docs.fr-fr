---
title: 'Préparation du débogage : Types de projet Visual C++ | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 592232277dd8eda337bf90e6df114c2a03e75c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502388"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Préparation du débogage : types de projets Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [préparation du débogage : Types de projets Visual C++](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-visual-cpp-project-types).  
  
Cette section explique le débogage de types de projets de base, créés par les modèles de projet [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
 Notez que ces types de projets qui créent des DLL en tant que leur sortie ont été regroupées dans [le débogage de projets de DLL](../debugger/debugging-dll-projects.md) en raison des fonctionnalités communes qu’ils partagent.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Paramètres de propriété recommandés](#BKMK_Recommended_Property_Settings)  
  
 [Projets Win32](#BKMK_Win32_Projects)  
  
-   [Pour déboguer une application Win32 C ou C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Pour définir manuellement une configuration Debug](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Applications Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Paramètres de propriété recommandés  
 Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage non managé. Les tableaux suivants présentent les paramètres de propriété recommandés. Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet non managés. Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propriétés de configuration &#124; C/C++ &#124; nœud optimisation  
  
|Nom de la propriété|Paramètre|  
|-------------------|-------------|  
|**Optimization**|La valeur **désactivé (/ 0d).** Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous trouvez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais n’oubliez pas que le code affiché dans le **désassemblage** fenêtre est générée à partir d’une source optimisée qui peut ne pas correspond ce que vous voyez dans votre source Windows. D’autres fonctionnalités, telles que l’exécution pas à pas, peuvent ne pas se comporter comme prévu.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propriétés de configuration &#124; l’éditeur de liens &#124; nœud débogage  
  
|Nom de la propriété|Paramètre|  
|-------------------|-------------|  
|**Générer des informations de débogage**|Vous devez toujours définir cette option **Oui (/Debug)** pour créer les symboles et fichiers nécessaires pour le débogage. Lorsque l'application passe en phase de production, vous pouvez la désactiver.|  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Projets Win32  
 Les applications Windows32 sont des programmes Windows traditionnels écrits en C ou C++. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est assez simple.  
  
 Les applications Win32 comprennent les applications MFC et les projets ATL. Elles utilisent les API Windows et parfois également MFC ou ATL, mais elles n'utilisent pas le Common Language Runtime (CLR). Toutefois, elles peuvent appeler du code managé qui utilise le CLR.  
  
 La procédure suivante explique comment déboguer un projet Win32 à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Une autre façon de déboguer une application Win32 consiste à démarrer l'application en dehors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puis de l'attacher. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Pour déboguer une application Win32 C ou C++  
  
1.  Ouvrez le projet dans Visual Studio.  
  
2.  Sur le **déboguer** menu, choisissez **Démarrer**.  
  
3.  Débogage en utilisant les techniques présentées dans [principes fondamentaux du débogueur](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Pour définir manuellement une configuration Debug  
  
1.  Dans le menu **vue**, cliquez sur **Pages de propriétés**.  
  
2.  Cliquez sur le **propriétés de Configuration** nœud pour l’ouvrir s’il n’est pas déjà  
  
3.  Sélectionnez **général**et définissez la valeur de la **sortie** ligne **déboguer**.  
  
4.  Ouvrez le **C/C++** nœud, puis sélectionnez **général**.  
  
     Dans le **déboguer** ligne que vous spécifiez le type d’informations devant être généré par le compilateur de débogage. Vous pouvez notamment choisir **la base de données de programme (/Zi)** ou **base de données de programme pour modifier & Continuer (/ Zi)**.  
  
5.  Sélectionnez **optimisation**, puis, dans le **optimisation** ligne, sélectionnez **désactivé (/ 0d)** dans la liste déroulante.  
  
     Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous constatez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais rappelez-vous que le code affiché dans la fenêtre Code Machine est généré à partir d'une source optimisée qui ne correspond peut-être pas à ce que vous voyez dans vos fenêtres sources. Certains fonctionnalités, telles que l’exécution pas à pas, peuvent afficher des points d’arrêt et un point d’exécution incorrects.  
  
6.  Ouvrez le **l’éditeur de liens** nœud, puis sélectionnez **débogage**. Dans la première **générer** ligne, sélectionnez **Oui (/Debug)** dans la liste déroulante. Sélectionnez toujours ce paramètre lorsque vous déboguez.  
  
 Pour plus d’informations, consultez[paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Applications Windows Forms (.NET)  
 Le **Windows Forms Application (.NET)** modèle crée un [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] application Windows Forms. Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est semblable à celui réalisé dans les applications Windows Forms managées.  
  
 Lorsque vous créez un projet Windows Forms à l'aide du modèle de projet, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres dans le  **\<nom_projet > Pages de propriétés** boîte de dialogue. Pour plus d’informations, consultez [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Une autre façon de déboguer une application Windows Forms consiste à démarrer l'application en dehors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et à l'attacher à celui-ci. Pour plus d’informations, consultez [attachement à un ou plusieurs programmes en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Dans cette rubrique](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Paramètres de projet pour une Configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Attachement à un ou plusieurs programmes en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)




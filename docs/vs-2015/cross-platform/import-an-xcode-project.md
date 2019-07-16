---
title: Importer un projet Xcode | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 4faa2ecae7f53d29e6aad92723ca6d12e50e2812
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150982"
---
# <a name="import-an-xcode-project"></a>Importer un projet Xcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual C++ pour le développement mobile multiplateforme prend en charge le déplacement de vos projets Xcode dans Visual Studio, où vous pouvez créer des bibliothèques multiplateformes et partager du code avec d’autres projets. L’Assistant Importation à partir de Xcode simplifie le processus d’importation de projets et de fractionnement du code C++ de vos cibles Xcode à utiliser en tant que bibliothèque statique ou projet de code partagé. Vous pouvez gérer votre code spécifique à iOS dans Visual Studio et continuer à utiliser Xcode pour effectuer des storyboards et des builds. Pour plus d’informations sur la façon de déplacer facilement du code entre Visual Studio et Xcode, consultez les détails relatifs au transfert de changements entre Xcode et Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Utilisation de l’Assistant Importation à partir de Xcode  
 Cette rubrique montre comment déplacer un projet Xcode dans Visual Studio pour tirer parti du partage de code et des solutions multiplateformes. Au préalable, vous devez jumeler votre Mac à Visual Studio pour pouvoir importer, exporter et générer votre projet. Pour obtenir des instructions sur la configuration du jumelage, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Vous devez également partager votre projet Xcode sur le réseau ou le déplacer vers votre ordinateur Visual Studio pour utiliser l’Assistant Importation à partir de Xcode.  
  
#### <a name="import-from-xcode"></a>Importer à partir de Xcode  
  
1. Dans le menu **Fichier**, choisissez **Nouveau**, **Importer**, **Importer à partir de Xcode**. Cela permet d’afficher la boîte de dialogue d’Assistant intitulée **Importer à partir de Xcode**.  
  
    ![Choisir le projet cible Xcode à importer](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. Dans le volet **Choisir un projet**, choisissez le bouton Parcourir pour sélectionner un fichier .pbxproj Xcode. Accédez au fichier projet via la boîte de dialogue **Sélectionner un fichier projet Xcode**, puis choisissez **Ouvrir**.  
  
    ![Sélectionner un fichier projet dans la boîte de dialogue Sélectionner un fichier projet Xcode](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    Dans l’Assistant Importation à partir de Xcode, choisissez **Suivant**.  
  
3. Dans le volet **Cibles de destination**, choisissez les cibles du projet Xcode à importer dans les projets Visual Studio. Les cibles Xcode sont semblables aux projets Visual Studio. Il s’agit pour la plupart d’un ensemble de codes et de ressources qui permettent de produire un fichier binaire. L’Assistant Importation à partir de Xcode autorise uniquement l’importation des cibles qui produisent un fichier binaire, mais pas une bibliothèque statique, en tant que cibles de destination. Les cibles de bibliothèque statique Xcode sont traitées à l’étape suivante.  
  
    ![Volet Cibles de destination de l’Assistant Importation à partir de Xcode](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    Pour chaque cible sélectionnée dans **Cibles à importer**, l’Assistant détecte automatiquement les fichiers de code C++ qui peuvent être fractionnés en projet de bibliothèque statique distinct, puis les place dans la section **Éléments de projet C++** . Le reste du code et des ressources est laissé dans la section **Éléments de projet Xcode**. Une fois que l’Assistant a effectué le processus d’importation, ils deviennent des projets de bibliothèque statique et d’application distincts dans Visual Studio. Par défaut, les cibles de test unitaire et de framework ne sont pas fractionnées en projets distincts par l’Assistant.  
  
    Pour changer les fichiers contenus dans chaque projet, utilisez les boutons de déplacement vers le haut et le bas. Une fois que la liste des fichiers de chaque projet vous convient, choisissez **Suivant** pour continuer.  
  
4. Dans le volet **Cibles de bibliothèques**, choisissez les cibles de bibliothèque statique du projet Xcode à importer dans les projets Visual Studio. Dans ce volet, vous pouvez choisir les fichiers à placer dans un projet de code partagé, et ceux à placer dans un projet de bibliothèque statique. Dans chacune des cibles de la liste **Cibles à importer**, vous pouvez contrôler les fichiers à placer dans les **Éléments de projet de code partagé** et les **Éléments de projet de bibliothèque statique** à l’aide des boutons de déplacement vers le haut et le bas.  
  
    ![Volet Cibles de bibliothèques de l’importation à partir de Xcode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Un projet de code partagé est un moyen de partager un ensemble de fichiers de code source entre plusieurs projets dans Visual Studio. Le code est généré dans le cadre du projet où il se trouve, et non en tant que projet à part entière. Comme les projets qui incluent du code partagé peuvent avoir différentes architectures et configurations, ceci est le meilleur moyen de fournir un projet unique qui contient le code à générer pour de nombreux genres de plateforme.  
  
    Une fois que la liste des fichiers de chaque projet vous convient, choisissez **Suivant** pour continuer.  
  
5. Vous pouvez utiliser le volet **Propriétés globales** pour définir un chemin de recherche de frameworks et un chemin de recherche de fichiers d’en-tête Include pour tous les projets iOS dans Visual Studio. Visual Studio utilise ces chemins pour la recherche du code source et pour IntelliSense. Ces chemins globaux sont utiles quand vous créez des projets iOS qui utilisent un ensemble commun d’en-têtes et de frameworks.  
  
    ![Volet Propriétés globales de l’importation à partir de Xcode](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Vous pouvez également définir ces chemins globaux dans Visual Studio, dans la boîte de dialogue **Options**. Pour les trouver, dans le menu **Outils**, sélectionnez **Options**. Dans la boîte de dialogue **Options**, développez **Multiplateforme**, **C++** , **iOS**, **Propriétés globales**.  
  
    Choisissez **Suivant** pour continuer.  
  
6. Le volet **Frameworks** permet de configurer les chemins utilisés par Visual Studio pour parcourir les éléments de votre projet, ainsi que pour IntelliSense. Les chemins doivent être accessibles à Visual Studio pour chaque framework référencé par votre projet Xcode. L’Assistant vérifie les références de framework dans les projets Xcode et indique si Visual Studio peut trouver le framework. Si vous avez déjà configuré un chemin dans les propriétés globales, il doit être découvert par Visual Studio. Les exceptions sont répertoriées dans la liste Frameworks. Pour chaque framework listé avec un X, indiquez un chemin accessible au PC afin de permettre à Visual Studio de trouver le framework. Vous pouvez utiliser le bouton Parcourir [...] pour afficher une boîte de dialogue **Sélectionner un dossier** et trouver le chemin. Le chemin du framework peut être celui d’une copie locale ou d’un partage réseau sur votre Mac.  
  
    ![Volet Frameworks de l’importation à partir de Xcode](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Choisissez **Suivant** pour continuer.  
  
7. Le volet **Paramètres du projet** vous permet de changer le framework et d’inclure les paramètres du chemin de recherche de fichiers d’en-tête Include pour chaque projet créé par l’Assistant. Utilisez ce volet pour définir les chemins spécifiques au projet qui diffèrent des paramètres globaux.  
  
    Pour définir un chemin spécifique à un projet, dans la liste déroulante **Projet de destination**, sélectionnez le fichier projet, puis définissez les valeurs des contrôles **Chemin de recherche de frameworks** et **Chemin de recherche de fichiers d’en-tête Include**. Vous pouvez utiliser le bouton Parcourir [...] près de chaque contrôle pour afficher une boîte de dialogue **Sélectionner un dossier** et trouver le chemin.  
  
    ![Volet Projets de l’importation à partir de Xcode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Si aucun Mac distant n’a été jumelé à ce PC dans Visual Studio, le lien Configurer une machine distante s’affiche. Pour obtenir des instructions sur la configuration du jumelage, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Pour importer le projet Xcode à l’aide des paramètres de l’Assistant, choisissez **Importer**.  
  
   L’Assistant Importation à partir de Xcode crée des projets dans Visual Studio qui correspondent aux cibles de projets Xcode sélectionnées. Le code partageable avec d’autres projets C++ est fractionné en projets de code partagé et de bibliothèque statique distincts. Le code restant est placé dans les projets de bibliothèque iOS et d’application qui peuvent être générés à distance par Visual Studio. Pour plus d’informations sur le déplacement du code entre Visual Studio et Xcode, consultez [Synchroniser les changements entre Xcode et Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

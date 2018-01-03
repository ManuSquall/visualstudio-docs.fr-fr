---
title: "Procédure pas à pas de préparation Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7554380435c77750eb48a5ce261cc0a2b3885ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="prepare-the-development-environment"></a>Préparer l’environnement de développement

Il existe certaines conditions préalables à l’utilisation du kit SDK Azure Mobile Client dans Unity.

## <a name="download-and-install-unity-2017"></a>Télécharger et installer Unity 2017

Unity 2017.1 ou version ultérieure est nécessaire. Tous les forfaits Unity fonctionnent avec la procédure pas à pas, notamment le forfait personnel gratuit. Téléchargez Unity à partir de https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Télécharger et installer Visual Studio 2017

La procédure pas à pas requiert Visual Studio 2017 15.3 et versions ultérieures, avec le développement de jeux avec une charge de travail Unity. Toutes les éditions de Visual Studio 2017 fonctionnent avec la procédure pas à pas, dont l’édition Community gratuite.

1. Téléchargez Visual Studio 2017 à partir de https://www.visualstudio.com/.

2. Installez Visual Studio 2017 et vérifiez que la charge de travail **Développement de jeux avec Unity** est activée.

 ![Sélectionner la charge de travail Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Si Visual Studio 2017 est déjà installé, vous pouvez afficher et modifier les charges de travail en exécutant le programme d’installation de Visual Studio.

## <a name="create-a-new-3d-unity-project"></a>Créer un projet Unity 3D

Lancez Unity et créez un projet 3D.

![Créer un projet Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Définir Visual Studio 2017 Preview comme éditeur de script

Il est possible que Visual Studio 2017 soit déjà défini comme éditeur de script externe d’Unity, mais il est important de vérifier que la version 15.3 Preview est sélectionnée.

1. Dans le menu **Edition** d’Unity, choisissez **Edition > Préférences...**.

  ![Ouvrir le menu Préférences](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Quand la fenêtre Préférences d’Unity s’affiche, sélectionnez l’onglet **Outils externes** sur le côté gauche.

3. Dans le menu déroulant **External Script Editor** (Éditeur de script externe), sélectionnez **Visual Studio 2017**.

  ![Définir l’éditeur de script externe](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Remplacer le runtime de script Unity par .NET 4.6
La procédure pas à pas requiert .NET 4.6 pour pouvoir utiliser le kit SDK Azure Mobile Client et ses dépendances.

1. Dans le menu **Fichier** d’Unity, choisissez **Fichier > Paramètres de build...**.

  ![Ouvrir les paramètres de build](media/vstu_azure-prepare-dev-environment-image4.png)

2. Cliquez sur le bouton **Paramètres du lecteur...**.

  ![Ouvrir les paramètres du lecteur](media/vstu_azure-prepare-dev-environment-image5.png)

3. Les paramètres du lecteur s’ouvrent dans la fenêtre Inspector (Inspecteur) d’Unity. Sous le titre **Configuration**, cliquez sur la liste déroulante **Scripting Runtime Version** (Version du runtime de script) et sélectionnez **Experimental (.NET 4.6 Equivalent)** (Expérimental [Équivalent .NET 4.6]). Une boîte de dialogue vous invitant à redémarrer Unity s’affiche. Sélectionnez **Redémarrer**.

  ![Sélectionner .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Ajouter une référence à System.Net.Http.dll

Le runtime de script équivalent .NET 4.6 Unity autorise l’utilisation du package System.Net.Http, nécessaire au kit SDK Azure Mobile Client. Le fichier DLL est inclus dans Unity, mais une référence doit être ajoutée pour l’utiliser.

1. Dans la fenêtre Projet de l’éditeur Unity, **cliquez avec le bouton droit** sur le dossier **Assets** (Ressources) et sélectionnez **Afficher dans l’Explorateur**.

  ![Afficher le dossier de ressources dans l’Explorateur](media/vstu_azure-prepare-dev-environment-image7.png)

2. Dans la fenêtre de l’Explorateur qui s’affiche, double-cliquez sur le répertoire **Assets** (Ressources) pour l’ouvrir.

3. Dans le répertoire de ressources, **cliquez avec le bouton droit** et sélectionnez **Nouveau > Document texte**.

4. Ouvrez le nouveau document texte dans un éditeur de texte et ajoutez la ligne : `-r:System.Net.Http.dll`

5. Enregistrez le document et fermez-le.

4. Renommez le nouveau document texte « **mcs.rsp** » et assurez-vous de supprimer l’extension de fichier .txt.

  * Si des extensions de fichier sont masquées, vous devez modifier vos options d’affichage des dossiers pour les afficher.
  * Ouvrez le menu Démarrer et tapez « options des dossiers » à rechercher. Sélectionnez **Options de l’Explorateur de fichiers**.
  * Sélectionnez l’onglet **View** (Affichage) et, dans les paramètres avancés, vérifiez que la case **Masquer les extensions des fichiers dont le type est connu** est décochée.

    ![Afficher le dossier de ressources dans l’Explorateur](media/vstu_azure-prepare-dev-environment-image8.png)

Une fois ces étapes effectuées, vous devez avoir un fichier nommé **mcs.rsp** avec la ligne `r:System.Net.Http.dll` dans le répertoire **Assets** (Ressources) racine de votre projet Unity.

>[!NOTE]
> La fonctionnalité de référence requiert Visual Studio Tools pour Unity 3.3 et versions ultérieures, qui figure dans la charge de travail Visual Studio 15.3 + Unity. Si cette étape ne fonctionne pas pour vous, vérifiez que la version correcte de VSTU est installée.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Ajouter le package NuGet Newtonsoft.Json à votre projet

Le kit SDK Azure Mobile Client nécessite le package Newtonsoft.Json. Malheureusement, Unity ne prend pas en charge NuGet. Si vous ouvrez un projet Unity dans Visual Studio et ajoutez un package avec NuGet, Unity l’effacera la prochaine fois que vous ouvrirez le projet dans l’éditeur Unity. Toutefois, les packages provenant de NuGet peuvent être ajoutés manuellement à un projet Unity.

1. Créez un dossier dans le répertoire de ressources de votre projet Unity appelé « **Packages NuGet** ». Cela concerne uniquement l’organisation.

2. Accédez à https://www.nuget.org/packages/Newtonsoft.Json/ et cliquez sur le bouton **Téléchargement manuel**. Téléchargez le fichier .nupkg.

  ![Afficher le dossier de ressources dans l’Explorateur](media/vstu_azure-prepare-dev-environment-image9.png)

3. Recherchez le fichier qui vient d’être téléchargé et remplacez l’extension de fichier .nupkg par **.zip**. Cela devrait vous permettre de visualiser et d’extraire les fichiers inclus comme tout autre fichier zip.

4. Ouvrez ou extrayez le répertoire zip et accédez à **\lib\net45**.

5. Copiez le fichier **Newtonsoft.Json.dll** dans le répertoire **Assets\Packages NuGet** de votre projet Unity.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Ajouter le package NuGet du kit SDK Azure Mobile Client à votre projet

Le kit SDK Azure Mobile Client contient des fonctions pour lire et écrire facilement dans les tables faciles Azure.

1. Accédez à https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ et cliquez sur le bouton **Téléchargement manuel**. Téléchargez le fichier .nupkg.

2. Recherchez le fichier qui vient d’être téléchargé et remplacez l’extension de fichier .nupkg par **.zip**. Cela devrait vous permettre de visualiser et d’extraire les fichiers inclus comme tout autre fichier zip.

3. Ouvrez ou extrayez le répertoire zip et accédez à **\lib\net45**.

4. Copiez le fichier **Microsoft.Azure.Mobile.Client.dll** dans le répertoire **Assets\Packages NuGet** de votre projet Unity.

>[!WARNING]
> Une fois ces étapes effectuées, veillez à redémarrer Unity et Visual Studio ou IntelliSense peut ne pas reconnaître les packages récemment ajoutés.

## <a name="conclusion"></a>Conclusion

Une fois ces étapes effectuées, votre projet Unity doit être configuré pour utiliser le kit SDK Azure Mobile Client. Vous pouvez tester votre environnement de développement en créant un script C# dans votre projet Unity, en l’ouvrant dans Visual Studio et en tapant les instructions using suivantes en haut :
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Si IntelliSense détecte ces instructions using, le programme d’installation s’est déroulé correctement. Si des erreurs s’affichent ou si IntelliSense ne reconnaît pas ces packages, essayez de redémarrer Unity et Visual Studio. Si cela ne fonctionne toujours pas, revoyez les étapes ci-dessus.

## <a name="next-step"></a>Étape suivante

* [Créer des classes de modèles de données](visual-studio-tools-for-unity-azure-data.md)

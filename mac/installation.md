---
title: Installer Visual Studio pour Mac
description: "Instructions sur l’installation de Visual Studio pour Mac et des composants supplémentaires nécessaires pour le développement multiplateforme."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 24d2fa5f9054e621cd5167692a2571e9275c2bae
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="setup-and-install-visual-studio-for-mac"></a>Configurer et installer Visual Studio pour Mac

## <a name="setup"></a>Installation

Pour commencer à développer des applications multiplateformes natives quand vous téléchargez Visual Studio pour Mac, vous devez installer et configurer un certain nombre de choses.

Pour travailler avec iOS dans Visual Studio, vous avez besoin des éléments suivants :

* un Mac avec macOS Sierra 10.12 ou ultérieur
* Xcode 8.3
* un ID Apple. Si vous n’avez pas déjà un ID Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

## <a name="install"></a>Installez

1. Téléchargez Visual Studio pour Mac à partir de [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Une fois le package d’installation téléchargé, cliquez sur le fichier **VisualStudioInstaller.dmg** pour monter le programme d’installation puis exécutez-le en double-cliquant sur le logo, comme illustré dans l’image suivante :

  ![Boîte de dialogue Programme d’installation](media/installer-image1.png)

3. Une boîte de dialogue d’alerte similaire à celle de l’image suivante peut s’afficher. Dans ce cas, cliquez sur **Ouvrir** :

  ![Boîte de dialogue d’alerte](media/installer-image2.png)

4. Le programme d’installation inspecte votre système pour vérifier quels composants doivent être installés ou mis à jour :

  ![Évaluation de votre système](media/installer-image3.png)

5. Une boîte de dialogue d’alerte vous est alors présentée, vous demandant d’accepter les termes du contrat de licence et de confidentialité. Cliquez sur le bouton **Continuer** pour accepter les termes du contrat :

  ![Boîte de dialogue Licence](media/installer-image4.png)

6. Le programme d’installation affiche une liste des composants nécessaires manquants, et qui doivent être téléchargés et installés. Sélectionnez les produits que vous voulez télécharger ici :

  ![Sélectionner des éléments](media/installer-image5.png)

  Cet écran d’installation affiche la version et la taille de chaque composant. Vous pouvez cliquer sur chaque composant pour afficher une liste des dépendances pour ce composant (pour Android), voir les packages supplémentaires qu’il télécharge (pour .NET Core), ou afficher les applications supplémentaires nécessaires (pour iOS et macOS) :

  ![Dépendances supplémentaires d’Android](media/installer-image6.png)

7. Une fois que vous êtes satisfait de votre sélection, sélectionnez le bouton **Installer et mettre à jour** pour démarrer le processus d’installation.

8. Le programme d’installation démarre le processus de téléchargement et d’installation des éléments sélectionnés :

  ![Démarrage de l’installation](media/installer-image7.png)

  ![Téléchargement de Xamarin.Mac](media/installer-image8.png)

  ![Fin de l’installation](media/installer-image9.png)

9. Vous pouvez être invité à élever les autorisations nécessaires pour des composants individuels nécessaires pour terminer l’installation. Entrez vos informations d’identification d’administrateur ici pour continuer le processus d’installation :

  ![Entrer les autorisations pour continuer avec le programme d’installation](media/installer-image10.png)

10. Une fois l’installation terminée, vous pouvez démarrer le développement d’applications dans Visual Studio en cliquant sur **Démarrer** :

  ![Ouvrir Visual Studio](media/installer-image11.png)

> [!NOTE]
Si vous avez choisi pas installer un outil ou une plateforme lors de l’installation d’origine (en la désélectionnant à l’étape 6), vous devez réexécuter le [programme d’installation](https://www.visualstudio.com/vs/) si vous voulez ajouter les composants plus tard.


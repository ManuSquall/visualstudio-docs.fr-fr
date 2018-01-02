---
title: Installer Visual Studio pour Mac | Microsoft Docs
description: "Instructions sur l’installation de Visual Studio pour Mac et des composants supplémentaires nécessaires pour le développement multiplateforme."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 7f91a28449ffad135058438ec767095818cc8527
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Configurer et installer Visual Studio pour Mac

## <a name="setup"></a>Installation

Pour commencer à développer des applications multiplateformes natives quand vous téléchargez Visual Studio pour Mac, vous devez installer et configurer un certain nombre de choses.

Pour travailler sur iOS dans Visual Studio, vous avez besoin des éléments suivants :

* Un Mac avec macOS Sierra 10.12 ou ultérieur
* Xcode 8.3 ou ultérieur. La dernière version stable est généralement recommandée.
* Un identifiant Apple. Si vous n’avez pas déjà un identifiant Apple, vous pouvez en créer un sur https://appleid.apple.com. Un ID Apple est nécessaire pour installer et se connecter à Xcode.

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

## <a name="manual-installation"></a>Installation manuelle

Si votre installation échoue ou si l’un des composants de votre installation échoue, vous pourrez peut-être résoudre le problème en effectuant une installation manuelle. Pour afficher les composants requis et télécharger chacun d’eux, effectuez les étapes suivantes :

1. Sur le second écran de Visual Studio Installer, accédez à la barre de menus et sélectionnez **Afficher les instructions d’installation manuelle** :

    ![Option montrant l’élément de menu d’installation manuelle](media/installer-image12.png)

2. Suivez les instructions pour télécharger et installer les composants manuellement :

  ![Boîte de dialogue d’installation manuelle](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Pour installer Visual Studio pour Mac derrière un pare-feu, certains points de terminaison doivent être rendus accessibles afin d’autoriser les téléchargements des outils requis et des mises à jour pour votre logiciel.

Configurez votre réseau de façon à autoriser l’accès aux emplacements suivants :

* [Points de terminaison de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)
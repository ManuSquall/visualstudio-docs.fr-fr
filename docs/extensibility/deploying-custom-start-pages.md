---
title: "Déploiement de Pages de démarrage personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>Déploiement de Pages de démarrage personnalisées
Vous pouvez déployer des Pages de démarrage personnalisées à l’aide de déploiement VSIX ou en copiant les fichiers aux emplacements appropriés sur l’ordinateur cible.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Déploiement VSIX à l’aide du modèle de projet de la Page de démarrage  
 Lorsque vous créez une Page de démarrage en utilisant le modèle de projet de Page de démarrage et ensuite générez le projet, Visual Studio crée un fichier .vsix que vous pouvez distribuer. Empaquetage d’une Page de démarrage dans un fichier .vsix offre les options suivantes pour le déploiement, en fonction de votre public ciblé :  
  
-   Vous pouvez placer le fichier .vsix sur un partage réseau ou sur un site Web public. Lorsqu’un utilisateur ouvre le fichier, la Page de démarrage est installée automatiquement.  
  
-   Vous pouvez télécharger le fichier .vsix pour le [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) de site Web afin que les utilisateurs peuvent les installer à l’aide de **le Gestionnaire d’extensions**.  
  
 Le modèle de Page de démarrage de projet crée une copie de la Page de démarrage de Visual Studio par défaut afin que vous puissiez modifier la copie et conserver l’original.  
  
 Vous pouvez obtenir le modèle de projet de Page de démarrage à l’aide de **le Gestionnaire d’extensions** ou en le téléchargeant à partir du site Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Déploiement VSIX sans utiliser le modèle de projet de la Page de démarrage  
 Déploiement VSIX requiert une extension pour être installés dans des dossiers qui sont reconnus par le processus d’inscription VSIX et par **le Gestionnaire d’extensions**. Étant donné que le modèle de projet de Page de démarrage spécifie déjà les dossiers appropriés, nous vous recommandons d’utiliser chaque fois que vous voulez créer une extension pour le déploiement VSIX. Toutefois, si vous avez un cas dans lequel vous ne pouvez pas utiliser le modèle, vous pouvez créer un déploiement VSIX sans l’utiliser.  
  
 Pour créer un déploiement VSIX sans utiliser le modèle de projet de Page de démarrage, commencez par créer un fichier .vsix pour la Page de démarrage d’une des deux façons suivantes :  
  
-   En ajoutant vos fichiers de Page de démarrage personnalisées à un projet VSIX vide. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
-   En créant manuellement un fichier .vsix. Pour plus d’informations, consultez [Comment : empaqueter manuellement une Extension (déploiement VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Pour Visual Studio de reconnaître une Page de démarrage, le `Content Element` du manifeste VSIX doit contenir un `CustomExtension Element` dont le `Type` attribut la valeur `"StartPage"`. Une extension de la Page de démarrage qui a été installée à l’aide de déploiement VSIX s’affiche dans le **personnaliser la Page de démarrage** liste sur le **démarrage** en tant que page d’options **[Extension installé]** *nom de l’Extension*.  
  
 Si le package de votre Page de démarrage inclut des assemblys, vous devez ajouter l’enregistrement de chemins de liaison afin qu’ils soient disponibles au démarrage de Visual Studio. Pour ce faire, assurez-vous que votre package inclut un fichier .pkgdef qui comporte les informations suivantes.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Déploiement VSIX pour tous les utilisateurs  
 Par défaut, les extensions déployées dans les packages VSIX installent uniquement pour l’utilisateur actuel. Vous pouvez effectuer une installation de la Page de démarrage pour tous les utilisateurs de l’ordinateur cible en créant un déploiement de tous les utilisateurs.  
  
##### <a name="to-create-an-all-users-deployment"></a>Pour créer un déploiement de tous les utilisateurs  
  
1.  Ouvrez le fichier extension.vsixmanifest en mode code.  
  
2.  Dans le `Identifier` élément du manifeste vsix, ajoutez un `AllUsers` élément qui a la valeur `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Cela entraîne l’installateur vsix demander des autorisations d’administrateur, puis installer les fichiers à \Common7\IDE\Extensions.  
  
3.  Ouvrez le fichier .pkgdef.  
  
4.  Modifier le .pkgdef pour définir la page de démarrage par défaut sous HKLM en ajoutant le code suivant, où *MyStartPage.xaml* est le nom du fichier .xaml qui contient votre Page de démarrage.  
  
     [$RootKey$ \StartPage\Default]  
  
     « Uri « = » $PackageFolder$\\*MyStartPage.xaml*»  
  
     Cela indique à Visual debout dans le nouvel emplacement de la Page de démarrage.  
  
## <a name="file-copy-deployment"></a>Déploiement de copie de fichier  
 Vous n’avez pas à créer un fichier .vsix pour déployer une Page de démarrage personnalisée. Au lieu de cela, vous pouvez copier le balisage et les fichiers de prise en charge directement dans le dossier \StartPages\ de l’utilisateur. Le **personnaliser la Page de démarrage** liste sur le **démarrage** page options répertorie tous les fichiers .xaml de ce dossier, ainsi que le chemin d’accès, par exemple, %USERPROFILE%\My Documents\Visual Studio *version*\StartPages\\*nom de fichier*.xaml. Si votre Page de démarrage inclut des références aux assemblys privés, vous devez les copier et les coller dans le dossier \PrivateAssemblies\.  
  
 Pour distribuer une Page de démarrage que vous avez créé sans emballage dans un fichier .vsix, nous recommandons que vous utilisez une stratégie de copie de fichier de base, par exemple, un script de commandes, ou toute autre technologie de déploiement qui vous permet de placer les fichiers dans les répertoires requis.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Pour installer manuellement une Page de démarrage personnalisée  
  
1.  Copiez le fichier .xaml qui contient le balisage de la Page de démarrage, ainsi que les fichiers autres que des assemblys et les coller dans le dossier \StartPages\ de l’utilisateur.  
  
2.  Si la Page de démarrage nécessite des assemblys, copiez-les et collez-les dans... \\ *Dossier d’installation de visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  Dans le **personnaliser la Page de démarrage** liste sur le **démarrage** options, sélectionnez la nouvelle Page de démarrage. Pour plus d’informations, consultez [personnalisation de la Page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la Page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Ajout du contrôle utilisateur à la Page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)

---
title: 'Procédure pas à pas : Création d’un programme d’installation personnalisé pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 597d0a29e153659359d3a6591970750bfd4de770
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405746"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Procédure pas à pas : Créer un programme d’installation personnalisé pour une application ClickOnce
N’importe quelle application ClickOnce selon un *.exe* fichier peut être installé et mis à jour par un programme d’installation personnalisé en mode silencieux. Un programme d’installation personnalisé peut implémenter l’expérience utilisateur personnalisée pendant l’installation, y compris les boîtes de dialogue personnalisées pour les opérations de maintenance et de sécurité. Pour effectuer des opérations d’installation, le programme d’installation personnalisé utilise la <xref:System.Deployment.Application.InPlaceHostingManager> classe. Cette procédure pas à pas montre comment créer un programme d’installation personnalisé qui installe en mode silencieux une application ClickOnce.

## <a name="prerequisites"></a>Prérequis

### <a name="to-create-a-custom-clickonce-application-installer"></a>Pour créer un programme d’installation des applications ClickOnce personnalisé

1. Dans votre application ClickOnce, ajoutez des références à System.Deployment et System.Windows.Forms.

2. Ajoutez une nouvelle classe à votre application et spécifier n’importe quel nom. Cette procédure pas à pas utilise le nom `MyInstaller`.

3. Ajoutez le code suivant `Imports` ou `using` instructions au début de votre nouvelle classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Ajoutez les méthodes suivantes à votre classe.

     Ces méthodes appellent <xref:System.Deployment.Application.InPlaceHostingManager> méthodes pour télécharger le manifeste de déploiement, déclarer des autorisations appropriées, demandez à l’utilisateur autorisé à installer, puis téléchargez et installez l’application dans le cache ClickOnce. Un programme d’installation personnalisé peut spécifier qu’une application ClickOnce est pré-approuvée, ou différer la décision d’approbation pour le <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> appel de méthode. Ce code préalablement fait confiance à l’application.

    > [!NOTE]
    > Les autorisations assignées en pré-approbation ne peut pas dépasser les autorisations du code de programme d’installation personnalisé.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Pour tenter de l’installation à partir de votre code, appelez le `InstallApplication` (méthode). Par exemple, si vous avez nommé votre classe `MyInstaller`, vous pouvez appeler `InstallApplication` de la façon suivante.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Étapes suivantes
 Une application ClickOnce peut également ajouter de logique de mise à jour personnalisée, y compris une interface utilisateur personnalisée à afficher pendant le processus de mise à jour. Pour plus d'informations, consultez <xref:System.Deployment.Application.UpdateCheckInfo>. Une application ClickOnce peut également supprimer l’entrée de menu de démarrage standard, raccourci et entrée Ajout / Suppression de programmes en utilisant un `<customUX>` élément. Pour plus d’informations, consultez [ \<entryPoint > élément](../deployment/entrypoint-element-clickonce-application.md) et <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Voir aussi
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > élément](../deployment/entrypoint-element-clickonce-application.md)
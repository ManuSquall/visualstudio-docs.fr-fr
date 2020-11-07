---
title: Créer un programme d’installation personnalisé pour l’application ClickOnce
description: Découvrez comment un programme d’installation personnalisé peut installer et mettre à jour silencieusement une application ClickOnce basée sur un fichier. exe.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 08b4adbaa7e7e25041f90628695de729aaff0d0d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349202"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Procédure pas à pas : créer un programme d’installation personnalisé pour une application ClickOnce
Toutes les applications ClickOnce basées sur un fichier *. exe* peuvent être installées sans assistance et mises à jour par un programme d’installation personnalisé. Un programme d’installation personnalisé peut implémenter l’expérience utilisateur personnalisée au cours de l’installation, y compris les boîtes de dialogue personnalisées pour les opérations de sécurité et de maintenance. Pour effectuer des opérations d’installation, le programme d’installation personnalisé utilise la <xref:System.Deployment.Application.InPlaceHostingManager> classe. Cette procédure pas à pas montre comment créer un programme d’installation personnalisé qui installe silencieusement une application ClickOnce.

## <a name="prerequisites"></a>Prérequis

### <a name="to-create-a-custom-clickonce-application-installer"></a>Pour créer un programme d’installation d’application ClickOnce personnalisé

1. Dans votre application ClickOnce, ajoutez des références à System. Deployment et System. Windows. Forms.

2. Ajoutez une nouvelle classe à votre application et spécifiez n’importe quel nom. Cette procédure pas à pas utilise le nom `MyInstaller`.

3. Ajoutez les `Imports` directives ou suivantes `using` en haut de votre nouvelle classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Ajoutez les méthodes suivantes à votre classe.

     Ces méthodes appellent des <xref:System.Deployment.Application.InPlaceHostingManager> méthodes pour télécharger le manifeste de déploiement, déclarer des autorisations appropriées, demander à l’utilisateur l’autorisation d’installer, puis télécharger et installer l’application dans le cache ClickOnce. Un programme d’installation personnalisé peut spécifier qu’une application ClickOnce est pré-approuvée ou peut reporter la décision d’approbation à l' <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> appel de méthode. Ce code préapprouve l’application.

    > [!NOTE]
    > Les autorisations affectées par l’approbation préalable ne peuvent pas dépasser les autorisations du code du programme d’installation personnalisé.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Pour tenter une installation à partir de votre code, appelez la `InstallApplication` méthode. Par exemple, si vous avez nommé votre classe `MyInstaller` , vous pouvez appeler `InstallApplication` de la façon suivante.

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
 Une application ClickOnce peut également ajouter une logique de mise à jour personnalisée, y compris une interface utilisateur personnalisée à afficher pendant le processus de mise à jour. Pour plus d'informations, consultez <xref:System.Deployment.Application.UpdateCheckInfo>. Une application ClickOnce peut également supprimer l’entrée de menu Démarrer standard, le raccourci et l’entrée ajout/suppression de programmes à l’aide d’un `<customUX>` élément. Pour plus d’informations, consultez [ \<entryPoint> Element](../deployment/entrypoint-element-clickonce-application.md) et <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>Voir aussi
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> appartient](../deployment/entrypoint-element-clickonce-application.md)

---
title: 'Procédure pas à pas : Création d’un programme d’installation personnalisé pour une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 16686b0bf53f9e1358d96a7abcfe95f8ed6aac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222766"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Procédure pas à pas : création d'un programme d'installation personnalisé pour une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N’importe quelle application ClickOnce basée sur un fichier .exe peut être installée en mode silencieux et mis à jour par un programme d’installation personnalisé. Un programme d’installation personnalisé peut implémenter l’expérience utilisateur personnalisée pendant l’installation, y compris les boîtes de dialogue personnalisées pour les opérations de maintenance et de sécurité. Pour effectuer des opérations d’installation, le programme d’installation personnalisé utilise la <xref:System.Deployment.Application.InPlaceHostingManager> classe. Cette procédure pas à pas montre comment créer un programme d’installation personnalisé qui installe en mode silencieux une application ClickOnce.  
  
## <a name="prerequisites"></a>Prérequis  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Pour créer un programme d’installation des applications ClickOnce personnalisé  
  
1.  Dans votre application ClickOnce, ajoutez des références à System.Deployment et System.Windows.Forms.  
  
2.  Ajoutez une nouvelle classe à votre application et spécifier n’importe quel nom. Cette procédure pas à pas utilise le nom `MyInstaller`.  
  
3.  Ajoutez le code suivant `Imports` ou `using` instructions au début de votre nouvelle classe.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Ajoutez les méthodes suivantes à votre classe.  
  
     Ces méthodes appellent <xref:System.Deployment.Application.InPlaceHostingManager> méthodes pour télécharger le manifeste de déploiement, déclarer des autorisations appropriées, demandez à l’utilisateur autorisé à installer, puis téléchargez et installez l’application dans le cache ClickOnce. Un programme d’installation personnalisé peut spécifier qu’une application ClickOnce est pré-approuvée, ou différer la décision d’approbation pour le <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> appel de méthode. Ce code préalablement fait confiance à l’application.  
  
    > [!NOTE]
    >  Les autorisations assignées en pré-approbation ne peut pas dépasser les autorisations du code de programme d’installation personnalisé.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5.  Pour tenter de l’installation à partir de votre code, appelez le `InstallApplication` (méthode). Par exemple, si vous avez nommé votre classe `MyInstaller`, vous pouvez appeler `InstallApplication` de la façon suivante.  
  
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
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > élément](../deployment/entrypoint-element-clickonce-application.md)




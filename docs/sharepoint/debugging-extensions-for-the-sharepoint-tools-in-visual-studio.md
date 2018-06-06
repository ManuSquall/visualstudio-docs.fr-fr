---
title: Déboguer des Extensions pour les outils SharePoint dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4e2e6f3858833be49caf59d4d53fc1f8a131f10
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765292"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Déboguer des extensions pour les outils SharePoint dans Visual Studio
  Vous pouvez déboguer des extensions des outils SharePoint dans l’instance expérimentale ou l’instance normale de Visual Studio. Si vous avez besoin dépanner le comportement d’une extension, vous pouvez également modifier les valeurs de Registre pour afficher les informations d’erreur supplémentaires et pour configurer la façon dont Visual Studio exécute les commandes SharePoint.  
  
## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Déboguer des extensions dans l’instance expérimentale de Visual Studio
 Pour protéger votre environnement de développement Visual Studio de toute altération accidentelle par les extensions non testées, le Kit de développement logiciel Visual Studio fournit une autre instance de Visual Studio, appelée la *instance expérimentale*, que vous pouvez utiliser Pour installer et tester des extensions. Développer de nouvelles extensions à l’aide de l’instance normale de Visual Studio, mais que vous déboguez et que vous les exécutez dans l’instance expérimentale. Pour plus d’informations, consultez [l’Instance expérimentale](/visualstudio/extensibility/the-experimental-instance).  
  
 Si vous utilisez un projet VSIX pour déployer votre extension, et le projet VSIX est le projet de démarrage dans votre solution, Visual Studio installe automatiquement et s’exécute l’extension dans l’instance expérimentale lorsque vous déboguez votre solution. Le projet de démarrage est le projet qui démarre lorsque vous déboguez une solution qui contient plusieurs projets. Pour plus d’informations sur l’utilisation d’un projet VSIX pour déployer votre extension, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

 Pour obtenir des exemples qui montrent comment déboguer différents types d’extensions dans l’instance expérimentale de Visual Studio, consultez les procédures suivantes :  
  
-   [Procédure pas à pas : extension d’un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, première partie](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Procédure pas à pas : création d’une étape de déploiement personnalisée pour des projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Procédure pas à pas : extension de l’Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Procédure pas à pas : appel du modèle d’objet client SharePoint à partir d’une extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Déboguer des extensions dans l’instance normale de Visual Studio
 Si vous souhaitez déboguer votre projet d’extension dans l’instance normale de Visual Studio, vous devez tout d’abord installer l’extension dans l’instance normale. Ensuite, attacher le débogueur à un deuxième processus Visual Studio. Une fois que vous avez terminé, vous pouvez supprimer l’extension afin qu’il n’est plus de charge sur l’ordinateur de développement.  
  
#### <a name="to-install-the-extension"></a>Pour installer l'extension  
  
1.  Fermez toutes les instances de Visual Studio.  
  
2.  Dans le dossier de sortie de génération pour le projet d’extension, ouvrez le *.vsix* fichier en double-cliquant dessus ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**:  
  
3.  Dans le **le programme d’installation de Visual Studio Extension** boîte de dialogue zone, sélectionnez l’édition de Visual Studio à laquelle vous souhaitez installer l’extension, puis choisissez le **installer** bouton.  
  
     Visual Studio installe les fichiers d’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*nom de l’auteur*\\*nom de l’extension* \\ *version*. Les trois derniers dossiers dans ce chemin d’accès sont construits à partir de la `Author`, `Name`, et `Version` éléments dans le *extension.vsixmanifest* fichier pour l’extension.  
  
4.  Une fois que Visual Studio installe l’extension, choisissez le **fermer** bouton.  
  
#### <a name="to-debug-the-extension"></a>Pour déboguer l’extension  
  
1.  Démarrez Visual Studio avec des privilèges d’administrateur et ouvrir le projet d’extension. Les étapes suivantes font référence à cette instance de Visual Studio en tant que le *tout d’abord l’instance*.  
  
2.  Démarrez une autre instance de Visual Studio avec des privilèges d’administrateur. Les étapes suivantes font référence à cette instance de Visual Studio en tant que le *seconde instance*.  
  
3.  Basculez vers la première instance de Visual Studio.  
  
4.  Dans la barre de menus, choisissez **déboguer**, **attacher au processus**.  
  
5.  Dans le **processus disponibles** , choisissez *devenv.exe*. Cette entrée fait référence à la deuxième instance de Visual Studio ; Il s’agit de l’instance que vous souhaitez déboguer votre extension de projet dans.  
  
6.  Choisissez le **attacher** bouton.  
  
     Visual Studio exécute le projet d’extension en mode débogage.  
  
7.  Basculez vers la deuxième instance de Visual Studio.  
  
8.  Créer un projet SharePoint qui charge votre extension. Par exemple, si vous déboguez une extension pour les éléments de projet de définition de liste, créez un **définition de liste** projet.  
  
9. Effectuer les étapes requises pour tester votre code d’extension.  
  
10. Lorsque vous avez fini de déboguer l’extension, fermez la deuxième instance de Visual Studio.  
  
#### <a name="to-remove-the-extension"></a>Pour supprimer l’extension  
  
1.  Dans Visual Studio, dans la barre de menus, choisissez **outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez le nom de l’extension, puis le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous voulez désinstaller l’extension.  
  
4.  Choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.  
  
## <a name="debug-sharepoint-commands"></a>Déboguer des commandes SharePoint
 Si vous souhaitez déboguer une commande SharePoint qui fait partie d’une extension des outils SharePoint, vous devez attacher le débogueur à la *vssphost4.exe* processus. Voici le processus hôte 64 bits qui exécute les commandes de SharePoint. Pour plus d’informations sur les commandes SharePoint et *vssphost4.exe*, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Pour attacher le débogueur au processus vssphost4.exe  
  
1.  Démarrez le débogage de votre extension dans l’instance expérimentale de Visual Studio ou l’instance normale de Visual Studio en suivant les instructions ci-dessus.  
  
2.  Dans l’instance de Visual Studio dans lequel vous exécutez le débogueur, sur la barre de menus, choisissez **déboguer**, **attacher au processus**.  
  
3.  Dans le **processus disponibles** , choisissez *vssphost.exe*.  
  
    > [!NOTE]  
    >  Si vssphost.exe n’apparaît pas dans la liste, vous devez démarrer le *vssphost4.exe* processus dans l’instance de Visual Studio dans lequel vous exécutez l’extension. En règle générale, cela en effectuant une action qui active de Visual Studio pour vous connecter au site SharePoint sur l’ordinateur de développement. Par exemple, Visual Studio démarre *vssphost4.exe* lorsque vous développez un nœud de connexion de site (nœud qui affiche une URL de site) sous le **connexions SharePoint** nœud dans le **l’Explorateur de serveurs**  fenêtre, ou lorsque vous ajoutez certains éléments de projet SharePoint, tels que **liste Instance** ou **récepteur d’événements** des éléments à un projet SharePoint.  
  
4.  Choisissez le **attacher** bouton.  
  
5.  Dans l’instance de Visual Studio est en cours de débogage, effectuez les étapes qui sont nécessaires pour exécuter votre commande.  
  
## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modifier les valeurs de Registre pour vous aider à déboguer des extensions d’outils SharePoint
 Lorsque vous déboguez une extension des outils SharePoint dans Visual Studio, vous pouvez modifier les valeurs dans le Registre pour vous aider à résoudre les problèmes de l’extension. Les valeurs se trouvent sous le **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** clé. Ces valeurs n’existent pas par défaut.  
  
 Pour aider à résoudre les problèmes de n’importe quelle extension des outils SharePoint, vous pouvez créer et définir la valeur EnableDiagnostics. Le tableau suivant décrit cette valeur.  
  
|Value|Description|  
|-----------|-----------------|  
|EnableDiagnostics|REG_DWORD qui spécifie si les messages de diagnostic sont affichés dans le **sortie** fenêtre.<br /><br /> Pour afficher les messages de diagnostic, définissez cette valeur sur 1. Pour arrêter l’affichage des messages, définissez cette valeur sur 0, ou supprimez cette valeur.<br /><br /> Pour écrire des messages à la **sortie** extension des outils de la fenêtre à partir de SharePoint, utilisez le service de projet SharePoint. Pour plus d’informations, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Si votre extension inclut une commande SharePoint, vous pouvez créer et définir des valeurs supplémentaires pour aider à résoudre les problèmes de la commande. Le tableau suivant décrit ces valeurs.  
  
|Value|Description|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|REG_DWORD qui spécifie s’il faut afficher une boîte de dialogue qui vous permet d’attacher le débogueur à *vssphost4.exe* dès qu’il démarre. Cela est utile si la commande que vous souhaitez déboguer est exécutée par vssphost.exe immédiatement après son démarrage, et il n’est pas suffisamment de temps pour attacher manuellement le débogueur avant l’exécution de la commande. Pour afficher la boîte de dialogue *vssphost4.exe* appelle la <xref:System.Diagnostics.Debugger.Break%2A> méthode lorsqu’il démarre.<br /><br /> Pour activer ce comportement, définissez cette valeur sur 1. Pour désactiver ce comportement, définissez cette valeur sur 0, ou supprimez cette valeur.<br /><br /> Si vous définissez cette valeur sur 1, vous pouvez souhaiter également augmenter la valeur HostProcessStartupTimeout vous-même suffisamment de temps pour attacher le débogueur avant Visual Studio attend *vssphost4.exe* pour signaler qu’il a démarré correctement.|  
|ChannelOperationTimeout|REG_DWORD qui spécifie la durée, en secondes, pendant laquelle Visual Studio attend une commande SharePoint à exécuter. Si la commande ne s’exécute pas dans le temps, un <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est 120 secondes.|  
|HostProcessStartupTimeout|REG_DWORD qui spécifie la durée, en secondes, que Visual Studio attend *vssphost4.exe* pour signaler qu’il a démarré correctement. Si *vssphost4.exe* ne signale pas de démarrage réussi dans le temps, un <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est 60 secondes.|  
|MaxReceivedMessageSize|REG_DWORD qui spécifie la taille maximale autorisée, en octets, des messages WCF passés entre Visual Studio et *vssphost4.exe*.<br /><br /> La valeur par défaut est 1 048 576 octets (1 Mo).|  
|MaxStringContentLength|REG_DWORD qui spécifie la taille maximale autorisée, en octets, de chaînes qui sont passées entre Visual Studio et *vssphost4.exe*.<br /><br /> La valeur par défaut est 1 048 576 octets (1 Mo).|  
  
## <a name="see-also"></a>Voir aussi
 [Extension des outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Déploiement d’extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  


---
title: Débogage d’extensions pour les outils SharePoint dans Visual Studio | Microsoft Docs
description: Extensions de débogage pour les outils SharePoint dans Visual Studio. Déboguez les extensions des outils SharePoint dans l’instance expérimentale ou l’instance régulière de VS.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ad95ce8b4ab9567f22748453ae59c258f24aa86
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671218"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Extensions de débogage pour les outils SharePoint dans Visual Studio
  Vous pouvez déboguer des extensions d’outils SharePoint dans l’instance expérimentale ou l’instance normale de Visual Studio. Si vous devez résoudre le comportement d’une extension, vous pouvez également modifier les valeurs de Registre pour afficher des informations supplémentaires sur l’erreur et configurer la façon dont Visual Studio exécute les commandes SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Extensions de débogage dans l’instance expérimentale de Visual Studio
 Pour protéger votre environnement de développement Visual Studio contre les dommages accidentels causés par des extensions non testées, le kit de développement logiciel (SDK) Visual Studio fournit une autre instance de Visual Studio, appelée *instance expérimentale*, que vous pouvez utiliser pour installer et tester des extensions. Vous développez de nouvelles extensions à l’aide de l’instance normale de Visual Studio, mais vous les déboguez et les exécutez dans l’instance expérimentale. Pour plus d’informations, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

 Si vous utilisez un projet VSIX pour déployer votre extension et que le projet VSIX est le projet de démarrage dans votre solution, Visual Studio installe et exécute automatiquement l’extension dans l’instance expérimentale quand vous déboguez votre solution. Le projet de démarrage est le projet qui démarre lorsque vous déboguez une solution qui contient plusieurs projets. Pour plus d’informations sur l’utilisation d’un projet VSIX pour déployer votre extension, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Pour obtenir des exemples qui montrent comment déboguer différents types d’extensions dans l’instance expérimentale de Visual Studio, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Procédure pas à pas : créer un élément de projet d’action personnalisée avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Procédure pas à pas : appel du modèle d’objet client SharePoint dans une extension de Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Extensions de débogage dans l’instance normale de Visual Studio
 Si vous souhaitez déboguer votre projet d’extension dans l’instance normale de Visual Studio, commencez par installer l’extension dans l’instance normale. Ensuite, attachez le débogueur à un deuxième processus Visual Studio. Une fois que vous avez terminé, vous pouvez supprimer l’extension afin qu’elle ne soit plus chargée sur l’ordinateur de développement.

#### <a name="to-install-the-extension"></a>Pour installer l'extension

1. Fermez toutes les instances de Visual Studio.

2. Dans le dossier de sortie de la génération pour le projet d’extension, ouvrez le fichier *. vsix* en double-cliquant dessus ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**:

3. Dans la boîte de dialogue **programme d’installation des extensions Visual Studio** , choisissez l’édition de Visual Studio sur laquelle vous voulez installer l’extension, puis cliquez sur le bouton **installer** .

     Visual Studio installe les fichiers d’extension dans%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions nom de l’extension de \\ *nom d’auteur* \\ *extension name* \\ *version*. Les trois derniers dossiers dans ce chemin d’accès sont construits à partir des `Author` `Name` éléments, et du `Version` fichier *extension. vsixmanifest* pour l’extension.

4. Une fois que Visual Studio a installé l’extension, cliquez sur le bouton **Fermer** .

#### <a name="to-debug-the-extension"></a>Pour déboguer l’extension

1. Ouvrez Visual Studio avec des privilèges d’administrateur et ouvrez le projet d’extension. Les étapes suivantes font référence à cette instance de Visual Studio en tant que *première instance*.

2. Démarrez une autre instance de Visual Studio avec des privilèges d’administrateur. Les étapes suivantes font référence à cette instance de Visual Studio en tant que *deuxième instance*.

3. Basculez vers la première instance de Visual Studio.

4. Dans la barre de menus, choisissez **Déboguer**, **attacher au processus**.

5. Dans la liste **processus disponibles** , choisissez *devenv.exe*. Cette entrée fait référence à la deuxième instance de Visual Studio. Il s’agit de l’instance dans laquelle vous souhaitez déboguer votre extension de projet.

6. Choisissez le bouton **attacher** .

     Visual Studio exécute le projet d’extension en mode débogage.

7. Basculez vers la deuxième instance de Visual Studio.

8. Créez un projet SharePoint qui charge votre extension. Par exemple, si vous déboguez une extension pour des éléments de projet de définition de liste, créez un projet de **définition de liste** .

9. Effectuez toutes les étapes requises pour tester le code de votre extension.

10. Lorsque vous avez terminé de déboguer l’extension, fermez la deuxième instance de Visual Studio.

#### <a name="to-remove-the-extension"></a>Pour supprimer l’extension

1. Dans Visual Studio, dans la barre de menus, choisissez **Outils**, **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez le nom de l’extension, puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension.

4. Choisissez le bouton **redémarrer maintenant** pour terminer la désinstallation.

## <a name="debug-sharepoint-commands"></a>Déboguer les commandes SharePoint
 Si vous souhaitez déboguer une commande SharePoint qui fait partie d’une extension d’outils SharePoint, vous devez attacher le débogueur au processus de *vssphost4.exe* . Il s’agit du processus hôte 64 bits qui exécute les commandes SharePoint. Pour plus d’informations sur les commandes et les *vssphost4.exe* SharePoint, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Pour attacher le débogueur au processus de vssphost4.exe

1. Commencez à déboguer votre extension dans l’instance expérimentale de Visual Studio ou l’instance normale de Visual Studio en suivant les instructions ci-dessus.

2. Dans l’instance de Visual Studio dans laquelle vous exécutez le débogueur, dans la barre de menus, choisissez **Déboguer**, **attacher au processus**.

3. Dans la liste **processus disponibles** , choisissez *vssphost.exe*.

    > [!NOTE]
    > Si vssphost.exe n’apparaît pas dans la liste, vous devez démarrer le processus de *vssphost4.exe* dans l’instance de Visual Studio dans laquelle vous exécutez l’extension. En règle générale, vous effectuez cette opération en effectuant une action qui entraîne la connexion de Visual Studio au site SharePoint sur l’ordinateur de développement. Par exemple, Visual Studio démarre *vssphost4.exe* lorsque vous développez un nœud de connexion de site (un nœud qui affiche une URL de site) sous le nœud **Connexions SharePoint** dans la fenêtre **Explorateur de serveurs** ou lorsque vous ajoutez certains éléments de projet SharePoint, tels que l' **instance de liste** ou les éléments de **récepteur d’événements** , à un projet SharePoint.

4. Choisissez le bouton **attacher** .

5. Dans l’instance de Visual Studio en cours de débogage, effectuez les étapes nécessaires à l’exécution de votre commande.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modifier les valeurs de Registre pour déboguer les extensions d’outils SharePoint
 Quand vous déboguez une extension des outils SharePoint dans Visual Studio, vous pouvez modifier les valeurs dans le registre pour vous aider à résoudre les problèmes liés à l’extension. Les valeurs existent sous la clé de **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** . Ces valeurs n’existent pas par défaut.

 Pour vous aider à résoudre les problèmes d’extension des outils SharePoint, vous pouvez créer et définir la valeur EnableDiagnostics. Le tableau suivant décrit cette valeur.

|Valeur|Description|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD qui spécifie si les messages de diagnostic s’affichent dans la fenêtre **sortie** .<br /><br /> Pour afficher les messages de diagnostic, définissez cette valeur sur 1. Pour ne plus afficher les messages, définissez cette valeur sur 0 ou supprimez cette valeur.<br /><br /> Pour écrire des messages dans la fenêtre **sortie** à partir d’une extension d’outils SharePoint, utilisez le service de projet SharePoint. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Si votre extension comprend une commande SharePoint, vous pouvez créer et définir des valeurs supplémentaires pour aider à résoudre les problèmes liés à la commande. Le tableau suivant décrit ces valeurs.

|Valeur|Description|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD qui spécifie s’il faut afficher une boîte de dialogue qui vous permet d’attacher le débogueur à *vssphost4.exe* dès son démarrage. Cela est utile si la commande que vous souhaitez déboguer est exécutée par vssphost.exe immédiatement après son démarrage, et qu’il n’y a pas assez de temps pour attacher manuellement le débogueur avant l’exécution de la commande. Pour afficher la boîte de dialogue, *vssphost4.exe* appelle la <xref:System.Diagnostics.Debugger.Break%2A> méthode au démarrage.<br /><br /> Pour activer ce comportement, définissez cette valeur sur 1. Pour désactiver ce comportement, définissez cette valeur sur 0 ou supprimez cette valeur.<br /><br /> Si vous définissez cette valeur sur 1, vous pouvez également augmenter la valeur HostProcessStartupTimeout pour vous accorder suffisamment de temps pour attacher le débogueur avant que Visual Studio n’attende *vssphost4.exe* pour signaler qu’il a démarré avec succès.|
|ChannelOperationTimeout|REG_DWORD qui spécifie la durée, en secondes, pendant laquelle Visual Studio attend l’exécution d’une commande SharePoint. Si la commande ne s’exécute pas dans le temps, une <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est 120 secondes.|
|HostProcessStartupTimeout|REG_DWORD qui spécifie la durée, en secondes, pendant laquelle Visual Studio attend *vssphost4.exe* pour signaler qu’il a démarré avec succès. Si *vssphost4.exe* ne signale pas un démarrage réussi dans le temps, une <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> est levée.<br /><br /> La valeur par défaut est de 60 secondes.|
|MaxReceivedMessageSize|REG_DWORD qui spécifie la taille maximale autorisée, en octets, des messages WCF transmis entre Visual Studio et *vssphost4.exe*.<br /><br /> La valeur par défaut est 1 048 576 octets (1 Mo).|
|MaxStringContentLength|REG_DWORD qui spécifie la taille maximale autorisée, en octets, des chaînes qui sont passées entre Visual Studio et *vssphost4.exe*.<br /><br /> La valeur par défaut est 1 048 576 octets (1 Mo).|

## <a name="see-also"></a>Voir aussi

- [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

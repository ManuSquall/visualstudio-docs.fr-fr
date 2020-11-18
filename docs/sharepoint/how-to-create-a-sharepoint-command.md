---
title: 'Comment : créer une commande SharePoint | Microsoft Docs'
description: Découvrez comment créer une commande SharePoint personnalisée pour appeler l’API du modèle d’objet serveur dans une extension d’outils SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41e4ab0fd70f4993d148cd5c67cb816bdc92e77a
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850700"
---
# <a name="how-to-create-a-sharepoint-command"></a>Comment : créer une commande SharePoint
  Si vous souhaitez utiliser le modèle d’objet serveur dans une extension d’outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l’API. Vous définissez la commande SharePoint dans un assembly qui peut appeler directement le modèle d’objet serveur.

 Pour plus d’informations sur l’objectif des commandes SharePoint, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Pour créer une commande SharePoint

1. Créez un projet de bibliothèque de classes avec la configuration suivante :

    - Cible le .NET Framework 3,5. Pour plus d’informations sur la sélection de la version cible de .NET Framework, consultez [Comment : cibler une version du .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Cible la plateforme AnyCPU ou x64. Par défaut, la plateforme cible pour les projets de bibliothèque de classes est AnyCPU. Pour plus d’informations sur la sélection de la plateforme cible, consultez [Comment : configurer des projets pour cibler des plateformes](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Vous ne pouvez pas implémenter une commande SharePoint dans le même projet que celui qui définit une extension d’outils SharePoint, car les commandes SharePoint ciblent le .NET Framework 3,5 et les extensions d’outils SharePoint ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Vous devez définir toutes les commandes SharePoint utilisées par votre extension dans un projet distinct. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. Dans une classe du projet, créez une méthode qui définit votre commande SharePoint. La méthode doit être conforme aux indications suivantes :

    - Il peut avoir un ou deux paramètres.

         Le premier paramètre doit être un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objet. Cet objet fournit le Microsoft. SharePoint. website ou Microsoft. SharePoint. SPWeb dans lequel la commande est exécutée. Il fournit également un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objet qui peut être utilisé pour écrire des messages dans la fenêtre **sortie** ou dans une fenêtre de **liste d’erreurs** dans Visual Studio.

         Le deuxième paramètre peut être un type de votre choix, mais ce paramètre est facultatif. Vous pouvez ajouter ce paramètre à votre commande SharePoint si vous avez besoin de transmettre des données de votre extension d’outils SharePoint à la commande.

    - Il peut avoir une valeur de retour, mais cela est facultatif.

    - Le deuxième paramètre et la valeur de retour doivent être un type qui peut être sérialisé par le Windows Communication Foundation (WCF). Pour plus d’informations, consultez [types pris en charge par le sérialiseur de contrat de données](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) et [utilisation de la classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - La méthode peut avoir n’importe quelle visibilité (**publique**, **interne** ou **privée**) et elle peut être statique ou non statique.

4. Appliquez <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> à la méthode. Cet attribut spécifie un identificateur unique pour la commande. Cet identificateur ne doit pas nécessairement correspondre au nom de la méthode.

     Vous devez spécifier le même identificateur unique lorsque vous appelez la commande à partir de votre extension d’outils SharePoint. Pour plus d’informations, consultez [Comment : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre une commande SharePoint avec l’identificateur `Contoso.Commands.UpgradeSolution` . Cette commande utilise des API dans le modèle objet serveur pour effectuer une mise à niveau vers une solution déployée.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 En plus du premier paramètre implicite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> , cette commande a également un paramètre de chaîne personnalisé qui contient le chemin d’accès complet du fichier. wsp qui est mis à niveau vers le site SharePoint. Pour voir ce code dans le contexte d’un exemple plus complet, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Compilation du code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Déploiement de la commande
 Pour déployer la commande, incluez l’assembly de commande dans le même [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (*VSIX*) avec l’assembly d’extension qui utilise la commande. Vous devez également ajouter une entrée pour l’assembly de commande dans le fichier extension. vsixmanifest. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Appeler les modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Comment : exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

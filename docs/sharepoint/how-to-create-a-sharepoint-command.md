---
title: 'Procédure : Créer une commande SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d804acd19d585bf9517ce9b8d771290a1f1c214a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435456"
---
# <a name="how-to-create-a-sharepoint-command"></a>Procédure : Créer une commande SharePoint
  Si vous souhaitez utiliser le modèle objet serveur dans une extension des outils SharePoint, vous devez créer un personnalisé *commande SharePoint* pour appeler l’API. Vous définissez la commande SharePoint dans un assembly qui peut appeler directement dans le modèle objet serveur.

 Pour plus d’informations sur la finalité des commandes SharePoint, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Pour créer une commande SharePoint

1. Créez un projet de bibliothèque de classes qui dispose de la configuration suivante :

    - Cible le .NET Framework 3.5. Pour plus d’informations sur la sélection du framework cible, consultez [Comment : Cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

    - Cible la AnyCPU ou x64 plateforme. Par défaut, la plateforme cible pour les projets de bibliothèque de classes est AnyCPU. Pour plus d’informations sur la sélection de la plateforme cible, consultez [Comment : Configurer des projets pour des plateformes cibles](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Vous ne pouvez pas implémenter une commande SharePoint dans le même projet qui définit une extension des outils SharePoint, car les commandes SharePoint ciblent le .NET Framework 3.5 et SharePoint tools extensions la cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Vous devez définir toutes les commandes SharePoint qui sont utilisés par votre extension dans un projet distinct. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Ajoutez des références aux assemblys suivants :

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. Dans une classe dans le projet, créez une méthode qui définit votre commande SharePoint. La méthode doit respecter les consignes suivantes :

    - Il peut avoir un ou deux paramètres.

         Le premier paramètre doit être un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objet. Cet objet fournit la Microsoft.SharePoint.SPSite Microsoft.SharePoint.SPWeb dans lequel la commande est exécutée. Il fournit également un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objet qui peut être utilisé pour écrire des messages dans la **sortie** fenêtre ou **liste d’erreurs** fenêtre dans Visual Studio.

         Le deuxième paramètre peut être un type de votre choix, mais ce paramètre est facultatif. Vous pouvez ajouter ce paramètre à votre commande SharePoint si vous avez besoin passer des données à partir de votre extension des outils SharePoint à la commande.

    - Il peut avoir une valeur de retour, mais cette étape est facultative.

    - La deuxième paramètre et valeur de retour doit être un type qui peut être sérialisé par Windows Communication Foundation (WCF). Pour plus d’informations, consultez [Types pris en charge par le sérialiseur de contrat de données](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) et [à l’aide de la classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - La méthode peut avoir aucune visibilité (**public**, **interne**, ou **privé**), et il peut être statique ou non statique.

4. Appliquer le <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> à la méthode. Cet attribut spécifie un identificateur unique pour la commande ; Cet identificateur n’a pas correspondre au nom de méthode.

     Vous devez spécifier le même identificateur unique lorsque vous appelez la commande à partir de votre extension des outils SharePoint. Pour plus d'informations, voir [Procédure : Exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Exemple
 L’exemple de code suivant montre une commande SharePoint avec l’identificateur `Contoso.Commands.UpgradeSolution`. Cette commande utilise les API dans le modèle objet serveur pour mettre à niveau vers une solution déployée.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 En plus de la première implicite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre, cette commande a également un paramètre de chaîne personnalisée qui contient le chemin d’accès complet du fichier .wsp qui est mis à niveau vers le site SharePoint. Pour voir ce code dans le contexte d’un exemple plus complet, consultez [procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Compilation du code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Déploiement de la commande
 Pour déployer la commande, incluez l’assembly de commande dans le même [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (*vsix*) package avec l’assembly d’extension qui utilise la commande. Vous devez également ajouter une entrée pour l’assembly de commande dans le fichier extension.vsixmanifest. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Guide pratique pour Exécuter une commande SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

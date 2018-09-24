---
title: 'Procédure pas à pas : Téléchargement d’assemblys satellites à la demande avec l’API du déploiement ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d7226726bc2eb9bbc53afa8920a26d342983af6
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281219"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procédure pas à pas : Téléchargement d’assemblys satellites à la demande avec l’API du déploiement ClickOnce
Les applications Windows Forms peuvent être configurées pour plusieurs cultures à l’aide d’assemblys satellites. Un *assembly satellite* contient des ressources d’application pour une culture autre que la culture par défaut de l’application.  
  
 Comme indiqué dans [applications ClickOnce localiser](../deployment/localizing-clickonce-applications.md), vous pouvez inclure plusieurs assemblys satellites pour plusieurs cultures au sein du même [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement. Par défaut, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] télécharge tous les assemblys satellites de votre déploiement sur l’ordinateur client, même si un seul client n’a probablement besoin que d’un assembly satellite.  
  
 Cette procédure pas à pas explique comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l’assembly dont a besoin un ordinateur client pour ses paramètres de culture actuels. La procédure suivante utilise les outils disponibles dans le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Vous pouvez également effectuer cette tâche dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consultez également [procédure pas à pas : télécharger des assemblys satellites à la demande avec l’API à l’aide du concepteur du déploiement ClickOnce](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) ou [procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API du déploiement ClickOnce à l’aide le concepteur](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
> [!NOTE]
>  À des fins de test, l’exemple de code suivant affecte par programmation la valeur `ja-JP`à la culture. Consultez la section « Étapes suivantes » plus loin dans cette rubrique pour plus d’informations sur l’adaptation de ce code à un environnement de production.  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique suppose que vous savez comment ajouter des ressources localisées à votre application à l’aide de Visual Studio. Pour obtenir des instructions détaillées, consultez [procédure pas à pas : les formulaires Windows localiser](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Pour télécharger des assemblys satellites à la demande  
  
1.  Ajoutez le code suivant à votre application pour activer le téléchargement à la demande des assemblys satellites.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Générer des assemblys satellites pour votre application à l’aide de [Resgen.exe (Resource File Generator)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Générer un manifeste d’application ou ouvrez votre manifeste d’application existant, à l’aide de *MageUI.exe*. Pour plus d’informations sur cet outil, consultez [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4.  Cliquez sur l’onglet **Files** .  
  
5.  Cliquez sur le **points de suspension** bouton (**...** ) et sélectionnez le répertoire contenant tous les assemblys et les fichiers, y compris les assemblys satellites que vous avez généré à l’aide de votre application *Resgen.exe*. (Un assembly satellite aura un nom sous la forme  *\<isoCode > \ApplicationName.resources.dll*, où \<isoCode > est un identificateur de langue au format RFC 1766.)  
  
6.  Cliquez sur **Populate** pour ajouter les fichiers à votre déploiement.  
  
7.  Cochez la case **Optional** pour chaque assembly satellite.  
  
8.  Définissez le champ de groupe pour chaque assembly satellite avec la valeur de son identificateur de langue ISO. Par exemple, pour un assembly satellite japonais, spécifiez le nom de groupe de téléchargement `ja-JP`. Cela permet au code ajouté à l’étape 1 de télécharger l’assembly satellite approprié, en fonction du paramètre de la propriété <xref:System.Threading.Thread.CurrentUICulture%2A> de l’utilisateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans un environnement de production, vous aurez probablement besoin de supprimer la ligne dans l’exemple de code qui définit <xref:System.Threading.Thread.CurrentUICulture%2A> avec une valeur spécifique, car les ordinateurs clients ont la valeur correcte définie par défaut. Quand votre application s’exécute sur un ordinateur client japonais, par exemple, <xref:System.Threading.Thread.CurrentUICulture%2A> aura la valeur `ja-JP` par défaut. La définition par programmation de cette valeur est un bon moyen de tester vos assemblys satellites avant de déployer votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Localiser des applications ClickOnce](../deployment/localizing-clickonce-applications.md)
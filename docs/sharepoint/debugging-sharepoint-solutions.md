---
title: "Débogage de Solutions SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14a3c7a2676c786e631b4c8b471272185b81e36c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-sharepoint-solutions"></a>Débogage de solutions SharePoint
  Vous pouvez déboguer des solutions SharePoint à l’aide de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Lorsque vous démarrez le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie les fichiers de projet sur le serveur SharePoint et ouvre une instance du site SharePoint dans le navigateur Web. Les sections suivantes expliquent comment déboguer des applications SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [L’activation du débogage](#EnableDebug)  
  
-   [Processus de déploiement et de débogage F5](#Deployment)  
  
-   [Fonctionnalités de projet SharePoint](#Features)  
  
-   [Débogage de workflows](#Workflow)  
  
-   [Débogage des récepteurs d’événements de fonctionnalité](#FeatureEvents)  
  
-   [L’activation des informations de débogage avancé](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a>L’activation du débogage  
 Lorsque vous déboguez tout d’abord une solution SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], une boîte de dialogue vous avertit que le fichier web.config n’est pas configuré pour activer le débogage. (Le fichier web.config est créé lorsque vous installez SharePoint server. Pour plus d’informations, consultez [utilisation des fichiers Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) La boîte de dialogue vous donne la possibilité d’exécuter le projet sans débogage ou en modifiant le fichier web.config pour activer le débogage. Si vous choisissez la première option, le projet s’exécute normalement. Si vous choisissez la deuxième option, le fichier web.config est configuré pour :  
  
-   Activer la pile des appels (`CallStack="true"`)  
  
-   Désactiver les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
-   Activer le débogage de compilation (`<compilation debug="true">`)  
  
 Le fichier web.config suit :  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 Pour annuler les modifications et désactiver le débogage, modifier les paramètres suivants [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dans le fichier web.config :  
  
-   Désactiver la pile des appels (`CallStack="false"`)  
  
-   Activer les erreurs personnalisées en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Désactiver le débogage de compilation (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a>Processus de déploiement et de débogage F5  
 Lorsque vous exécutez votre projet SharePoint en mode débogage, le processus de déploiement SharePoint effectue les tâches suivantes :  
  
1.  Exécute les commandes de prédéploiement personnalisables.  
  
2.  Crée un fichier de package (.wsp) solution Web à l’aide de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] commandes. Le fichier .wsp comprend tous les fichiers nécessaires et des fonctionnalités. Pour plus d’informations, consultez [vue d’ensemble des Solutions](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Si la solution SharePoint est une solution de batterie, il recycle le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications pour le site spécifié [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Cette étape de libérer les fichiers verrouillés par le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus de travail.  
  
4.  Si une version antérieure du package existe déjà, retire la version précédente des fonctionnalités et des fichiers dans le fichier .wsp. Cette étape désactive les fonctionnalités, désinstalle le package de solution, puis supprime le package de solution sur le serveur SharePoint.  
  
5.  Installe la version actuelle de fonctionnalités et des fichiers dans le fichier .wsp. Cette étape ajoute et installe la solution sur le serveur SharePoint.  
  
6.  Pour les workflows, installe l’assembly de flux de travail. Vous pouvez changer son emplacement à l’aide de la *emplacement de l’Assembly* propriété.  
  
7.  Active la fonctionnalité du projet dans SharePoint si l’étendue est le Site ou Web. Fonctionnalités dans les étendues de la batterie de serveurs et WebApplication ne sont pas activées.  
  
8.  Pour les workflows, associe le flux de travail à la bibliothèque SharePoint, liste ou le site que vous avez sélectionné dans le **Assistant Personnalisation de SharePoint**.  
  
    > [!NOTE]  
    >  Cette association se produit uniquement si vous avez sélectionné **automatiquement association de flux de travail** dans l’Assistant.  
  
9. Exécute les commandes de post-déploiement personnalisables.  
  
10. Attache le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] du débogueur pour le [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] processus (w3wp.exe). Si le type de projet vous permet de modifier le *Solution bac à sable* propriété et sa valeur est définie sur **true**, puis le débogueur s’attache à un autre processus (SPUCWorkerProcess.exe). Pour plus d’informations, consultez [considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Démarre le débogueur JavaScript si la solution SharePoint est une solution de batterie de serveurs.  
  
12. Affiche la bibliothèque appropriée, une liste ou une page de site dans le navigateur Web.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]affiche un message d’état dans la fenêtre sortie après que chaque tâche est terminée. Si une tâche ne peut pas être effectuée, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d’erreur dans la fenêtre liste d’erreurs.  
  
##  <a name="Features"></a>Fonctionnalités de projet SharePoint  
 Une fonctionnalité est une unité portable et modulaire de fonctionnalités qui simplifient la modification des sites à l’aide de définitions de site. Il est également un package de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] éléments (WSS) qui peuvent être activés pour une portée spécifique et qui permet aux utilisateurs de réaliser une tâche ou un objectif particulier. Les modèles sont déployés en tant que fonctionnalités.  
  
 Lorsque vous exécutez un projet en mode débogage, le processus de déploiement crée un dossier dans le *fonctionnalité* répertoire %CommonProgramFiles%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES. Les noms de fonction ont le format *nom du projet*_Feature*x*, telles que TestProject_Feature1.  
  
 Dossier de la solution dans le répertoire de fonctionnalités contient un *la définition de fonctionnalité* fichier et un *définition de workflow* fichier. Le fichier de définition de fonctionnalité (Feature.xml) décrit les fichiers en fonction de son fichier de définition de projet (Elements.xml) décrit le modèle de projet. Elements.XML peut être localisé dans **l’Explorateur de solutions**, mais Feature.xml est généré lorsque le package de solution est créé. Pour plus d’informations sur ces fichiers, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a>Débogage de Workflows  
 Lorsque vous déboguez des projets de flux de travail, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le modèle de flux de travail (selon son type) à une bibliothèque ou à une liste. Vous pouvez ensuite démarrer le modèle de flux de travail manuellement ou en ajoutant ou en mettant à jour un élément. Vous pouvez ensuite utiliser [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déboguer le flux de travail.  
  
> [!NOTE]  
>  Si vous ajoutez des références à d’autres assemblys, assurez-vous que ces assemblys sont installés dans le global assembly cache ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Sinon, la solution de flux de travail échoue. Pour plus d’informations sur la façon d’installer des assemblys, consultez [démarrer manuellement un flux de travail sur un document ou un élément](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Toutefois, le processus de déploiement ne démarre pas le flux de travail. Vous devez démarrer le flux de travail à partir du site SharePoint Web. Vous pouvez également démarrer le flux de travail à l’aide d’une application cliente comme Microsoft Office Word 2010, ou à l’aide du code côté serveur distinct. Utilisez une des approches spécifiés dans le **Assistant Personnalisation de SharePoint**.  
  
 Par exemple, si vous avez spécifié que le flux de travail peut être démarré manuellement, démarrez le flux de travail directement à partir de l’élément dans la liste ou bibliothèque. Pour plus d’informations sur la façon de démarrer un flux de travail manuellement, consultez [démarrer manuellement un flux de travail sur un élément de document](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a>Débogage des récepteurs d’événements de fonctionnalité  
 Par défaut, lorsque vous exécutez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] application SharePoint, ses fonctionnalités sont automatiquement activées sur le serveur SharePoint. Toutefois, cela pose des problèmes lorsque vous déboguez des récepteurs d’événements de fonctionnalité, car lorsque la fonctionnalité est activée par [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il s’exécute dans un processus autre que le débogueur. Cela signifie que certaines fonctionnalités de débogage, telles que des points d’arrêt, ne fonctionnent pas correctement.  
  
 Pour désactiver l’activation automatique de la fonctionnalité dans SharePoint et permettre un débogage approprié des récepteurs d’événements de fonctionnalité, affectez la valeur du projet **Configuration de déploiement Active** propriété **aucune Activation** avant le débogage. Ensuite, une fois que vous commencez à déboguer votre application SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]manuellement activer la fonctionnalité dans SharePoint. Pour activer la fonctionnalité, ouvrez le **Actions du Site** menu dans SharePoint, choisissez **paramètres du Site**, choisissez le **gérer les fonctionnalités du Site** lier, puis choisissez le **Activer** bouton en regard de la fonctionnalité, pour continuer le débogage normalement.  
  
##  <a name="EnhancedDebug"></a>L’activation des informations de débogage avancé  
 En raison des interactions parfois complexes entre la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processus (devenv.exe), le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le processus hôte (vssphost4.exe) SharePoint, SharePoint et la couche de WCF, diagnostiquer les erreurs qui se produisent lors de la génération, déploiement et ainsi de suite peut être un demande d’accès. Pour vous aider à résoudre ces erreurs, vous pouvez activer les informations de débogage avancé. Pour ce faire, accédez à la clé de Registre suivante dans le Registre Windows :  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 Si le « EnableDiagnostics » **REG_DWORD** valeur n’existe pas déjà, ne créer manuellement. Définissez la valeur « EnableDiagnostics » sur « 1 ».  
  
 La valeur clée 1 causes pile trace informations apparaissent dans le **sortie** fenêtre chaque fois que les erreurs de système de projet se produisent pendant l’exécution [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour désactiver les informations de débogage avancé, définissez EnableDiagnostics ramenez-la à 0, ou supprimer la valeur.  
  
 Pour plus d’informations sur les autres clés de Registre SharePoint, consultez [débogage d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  
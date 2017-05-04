---
title: "D&#233;bogage de solutions SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, débogage"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# D&#233;bogage de solutions SharePoint
  Vous pouvez déboguer des solutions SharePoint au moyen du débogueur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Lorsque vous lancez la procédure de débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie les fichiers de projet sur le serveur SharePoint, puis ouvre une instance du site SharePoint dans le navigateur Web.  Les sections suivantes expliquent comment déboguer des applications SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Activation du débogage](#EnableDebug)  
  
-   [Débogage F5 et processus de déploiement](#Deployment)  
  
-   [Fonctionnalités de projet SharePoint](#Features)  
  
-   [Débogage de flux de travail](#Workflow)  
  
-   [Débogage des récepteurs d'événements de fonctionnalité](#FeatureEvents)  
  
-   [Activation des informations de débogage avancé](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Activation du débogage  
 La première fois que vous déboguez une solution SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], une boîte de dialogue vous informe que le fichier web.config. n'est pas configuré pour activer le débogage. Ce fichier est créé au moment de l'installation du serveur SharePoint.  Pour plus d'informations, consultez [Utilisation des fichiers Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).\) La boîte de dialogue vous donne le choix entre deux options : exécuter le projet sans débogage ou modifier le fichier web.config. pour activer le débogage.  Dans le premier cas, le projet s'exécute normalement.  Dans le deuxième cas, le fichier web.config. est configuré de façon à :  
  
-   Activer la pile des appels \(`CallStack="true"`\)  
  
-   Désactiver les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(`<customErrors mode="Off" />`\)  
  
-   Activer le débogage de compilation \(`<compilation debug="true">`\)  
  
 Le fichier web.config. qui en résulte est le suivant :  
  
```  
  
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
  
 Pour annuler les modifications et désactiver le débogage, modifiez le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] suivant dans le fichier web.config. :  
  
-   Désactivez la pile des appels \(`CallStack="false"`\)  
  
-   Activez les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(`<customErrors mode="On" />`\)  
  
-   Désactivez le débogage de compilation \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> Débogage F5 et processus de déploiement  
 Lorsque vous exécutez votre projet SharePoint en mode débogage, le processus de déploiement SharePoint effectue les tâches suivantes :  
  
1.  Il exécute les commandes de prédéploiement personnalisables.  
  
2.  Il crée un fichier de package de solution Web \(.wsp\) à l'aide des commandes [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Le fichier .wsp comprend l'ensemble des fichiers et fonctionnalités nécessaires.  Pour plus d'informations, consultez [Vue d'ensemble des solutions](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Si la solution SharePoint est une solution de batterie, il recycle le pool d'applications [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pour le site [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] spécifié.  Cette étape permet de libérer les fichiers verrouillés par le processus de travail [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].  
  
4.  S'il existe une version antérieure du package, il retire la version précédente des fonctionnalités et des fichiers dans le fichier .wsp.  Cette étape a pour effet de désactiver les fonctionnalités, de désinstaller le package de solution, puis de supprimer le package de solution sur le serveur SharePoint.  
  
5.  Il installe la version actuelle des fonctionnalités et des fichiers dans le fichier .wsp.  Cette étape ajoute et installe la solution sur le serveur SharePoint.  
  
6.  Dans le cas des flux de travail, il installe l'assembly de flux de travail.  Vous pouvez modifier son emplacement à l'aide de la propriété *Assembly Location*.  
  
7.  Il active la fonctionnalité du projet dans SharePoint si la portée correspond à Site ou Web.  Les fonctionnalités des portées Batterie et WebApplication ne sont pas activées.  
  
8.  Pour les flux de travail, il associe le flux de travail à la bibliothèque, à la liste ou au site SharePoint que vous avez sélectionné dans l'**Assistant Personnalisation de SharePoint**.  
  
    > [!NOTE]  
    >  Cela n'est possible que si vous avez sélectionné **Associer automatiquement le flux de travail** dans l'Assistant.  
  
9. Il exécute les commandes de post\-déploiement personnalisables.  
  
10. Attache [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le débogueur [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] au processus \( w3wp.exe \).  Si le type de projet vous autorise à changer les propriétés *Sandboxed Solution* et si sa valeur est définie à **true**, alors le déboguer attache à un différent processus \(SPUCWorkerProcess.exe\).  Pour plus d'informations, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Il démarre le débogueur JavaScript si la solution SharePoint est une solution de batterie.  
  
12. Il affiche la bibliothèque, la liste ou la page de site appropriée dans le navigateur Web.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d'état dans la fenêtre Sortie à l'issue de chaque tâche.  Lorsqu'une tâche ne peut pas être effectuée, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d'erreur dans la fenêtre Liste d'erreurs.  
  
##  <a name="Features"></a> Fonctionnalités de projet SharePoint  
 Une fonctionnalité est une unité portable et modulaire de fonctionnalités qui simplifient la modification de sites via des définitions de site.  Il s'agit également d'un package d'éléments [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\) qui peuvent être activés pour une portée spécifique et qui permettent à des utilisateurs de réaliser une tâche ou un objectif particulier.  Les modèles sont déployés comme des fonctionnalités.  
  
 Lorsque vous exécutez un projet en mode débogage, le processus de déploiement crée un dossier dans le répertoire de *fonctionnalités* sous %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES.  Les noms des fonctionnalités ont le format *project name*\_Feature*x*, tel que TestProject\_Feature1.  
  
 Le dossier de la solution dans le répertoire de fonctionnalités contient un fichier de *définition de fonctionnalité* et un fichier de *définition de flux de travail*.  Le fichier de définition de fonctionnalité \(Feature.xml\) décrit les fichiers dans la fonctionnalité du projet.Le fichier de définition de projet \(Elements.xml\) décrit le modèle de projet.  Elements.xml peut être localisé dans l'**Explorateur de solutions**, mais Feature.xml est généré au moment de la création du package de solution.  Pour plus d'informations sur ces fichiers, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Débogage de flux de travail  
 Lorsque vous déboguez des projets de flux de travail, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le modèle de flux de travail \(selon son type\) à une bibliothèque ou à une liste.  Vous pouvez démarrer ensuite le modèle de flux de travail de façon manuelle ou en ajoutant ou mettant à jour un élément.  Il suffit ensuite d'utiliser [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déboguer le flux de travail.  
  
> [!NOTE]  
>  Si vous ajoutez des références à d'autres assemblys, assurez\-vous que ces assemblys sont installés dans le Global Assembly Cache \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  Sinon, la solution de flux de travail échouera.  Pour plus d'informations sur l'installation d'assemblys, consultez [Démarrer manuellement un flux de travail sur un document ou un élément](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Le processus de déploiement n'a pas pour effet de lancer le flux de travail.  Vous devez démarrer le flux de travail à partir du site Web SharePoint.  Vous pouvez également démarrer le flux de travail en utilisant une application cliente telle que Microsoft Office Word 2010 ou en utilisant du code distinct côté serveur.  Utilisez l'une des approches indiquées dans l'**Assistant Personnalisation de SharePoint**.  
  
 Par exemple, si vous avez spécifié que le flux de travail peut être démarré manuellement, démarrez directement le flux de travail à partir de l'élément de la bibliothèque ou de la liste.  Pour plus d'informations sur le démarrage manuel d'un flux de travail, voir [Démarrez manuellement un flux de travail sur un élément du document](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Débogage des récepteurs d'événements de fonctionnalité  
 Par défaut, lorsque vous exécutez une application SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ses fonctionnalités sont automatiquement activées sur le serveur SharePoint.  Toutefois, cela pose des problèmes si vous déboguez des récepteurs d'événements de fonctionnalité. En effet, une fonctionnalité activée par [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s'exécute dans un processus différent du débogueur.  Cela signifie que certaines fonctionnalités de débogage, telles que les points d'arrêt, ne fonctionneront pas correctement.  
  
 Pour désactiver l'activation automatique de la fonctionnalité dans SharePoint et permettre un débogage approprié des récepteurs d'événements de fonctionnalité, affectez à la propriété **Configuration de déploiement active** du projet la valeur **Aucune activation** avant de procéder au débogage.  Puis, après vous commencer le déboguage de votre application Sharepoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], activez manuellement la fonctionnalité dans SharePoint.  Pour activer la fonctionnalité, ouvrir le menu **Paramètres du site** dans SharePoint, choisissez **Paramètres du Site**, choisissez le lien **Gérer les fonctionnalités du Site**, puis choisissez le bouton **Activer** à coté de la fonctionnalité, pour continuer normalement le déboguage.  
  
##  <a name="EnhancedDebug"></a> Activation des informations de débogage avancé  
 En raison des interactions parfois complexes entre le processus [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(devenv.exe\), le processus hôte Sharepoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(vssphost4.exe\), SharePoint et la couche WCF, il n'est pas toujours facile de diagnostiquer les erreurs qui se produisent lors de la génération, du déploiement ou d'autres phases.  Pour résoudre plus facilement ce type d'erreur, vous pouvez activer les informations de débogage avancé.  Pour cela, accédez à la clé de Registre suivante dans le Registre Windows :  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 Si « EnableDiagnostics » **REG\_DWORD** n'existe pas, créez le manuellement.  Définissez la valeur de « EnableDiagnostics » à « 1 ".  
  
 Lorsque la valeur de clé est 1, les informations de trace de pile s'affichent dans la fenêtre **Sortie** à chaque fois qu'une erreur de système de projet se produit lorsque vous exécutez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour désactiver les informations de débogage avancé, rétablissez la valeur de EnableDiagnostics à 0, ou supprimez la.  
  
 Pour plus d'informations sur les autres clés de Registre SharePoint, consultez [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  
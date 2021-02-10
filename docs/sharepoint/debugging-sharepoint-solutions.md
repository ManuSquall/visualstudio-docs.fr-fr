---
title: Débogage de solutions SharePoint | Microsoft Docs
description: Déboguez des solutions SharePoint à l’aide du débogueur Visual Studio. Explorez le processus de débogage et de déploiement F5, déboguez les flux de travail et déboguez les récepteurs d’événements de fonctionnalité.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f1a6abfbafcbafb9daa52fdc6af85156700efef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948945"
---
# <a name="debug-sharepoint-solutions"></a>Déboguer des solutions SharePoint
  Vous pouvez déboguer des solutions SharePoint à l’aide du [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Lorsque vous démarrez le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie les fichiers projet sur le serveur SharePoint, puis ouvre une instance du site SharePoint dans le navigateur Web. Les sections suivantes expliquent comment déboguer des applications SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Activer le débogage](#enable-debugging)

- [Processus de débogage et de déploiement F5](#f5-debug-and-deployment-process)

- [Fonctionnalités de projet SharePoint](#sharepoint-project-features)

- [Déboguer des workflows](#debug-workflows)

- [Déboguer les récepteurs d’événements de fonctionnalité](#debug-feature-event-receivers)

- [Activer les informations de débogage Ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Activer le débogage
 Lorsque vous déboguez pour la première fois une solution SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , une boîte de dialogue vous avertit que le fichier web.config n’est pas configuré pour activer le débogage. (Le fichier web.config est créé lorsque vous installez SharePoint Server. Pour plus d’informations, consultez [utilisation de fichiers Web.config](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) La boîte de dialogue vous donne la possibilité d’exécuter le projet sans débogage ou de modifier le fichier web.config pour activer le débogage. Si vous choisissez la première option, le projet s’exécute normalement. Si vous choisissez la deuxième option, le fichier web.config est configuré pour :

- Activer la pile des appels ( `CallStack="true"` )

- Désactiver les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Activer le débogage de compilation ( `<compilation debug="true">` )

  Le fichier web.config résultant est le suivant :

```xml
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

 Pour annuler les modifications et désactiver le débogage, modifiez les éléments suivants [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dans le fichier web.config :

- Désactiver la pile des appels ( `CallStack="false"` )

- Activer les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Désactiver le débogage de compilation ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>Processus de débogage et de déploiement F5
 Lorsque vous exécutez votre projet SharePoint en mode débogage, le processus de déploiement SharePoint effectue les tâches suivantes :

1. Exécute les commandes de pré-déploiement personnalisables.

2. Crée un fichier de package de solution Web (. wsp) à l’aide de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] commandes. Le fichier. wsp contient tous les fichiers et fonctionnalités nécessaires. Pour plus d’informations, consultez [vue d’ensemble des solutions](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Si la solution SharePoint est une solution de batterie de serveurs, recycle le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications pour le site spécifié [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . Cette étape libère les fichiers verrouillés par le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus de travail.

4. Si une version précédente du package existe déjà, retire la version précédente des fonctionnalités et des fichiers dans le fichier. wsp. Cette étape désactive les fonctionnalités, désinstalle le package de solution, puis supprime le package de solution sur le serveur SharePoint.

5. Installe la version actuelle des fonctionnalités et des fichiers dans le fichier. wsp. Cette étape ajoute et installe la solution sur le serveur SharePoint.

6. Pour les flux de travail, installe l’assembly de flux de travail. Vous pouvez modifier son emplacement à l’aide de la propriété d’emplacement de l' *assembly* .

7. Active la fonctionnalité du projet dans SharePoint si l’étendue est site ou Web. Les fonctionnalités des étendues de batterie de serveurs et WebApplication ne sont pas activées.

8. Pour les flux de travail, associe le flux de travail à la bibliothèque, à la liste ou au site SharePoint que vous avez sélectionné dans l' **Assistant Personnalisation de SharePoint**.

   > [!NOTE]
   > Cette association se produit uniquement si vous avez sélectionné **associer automatiquement le flux de travail** dans l’Assistant.

9. Exécute les commandes de redémarrage personnalisables.

10. Attache le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur au [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] processus (*w3wp.exe*). Si le type de projet vous permet de modifier la propriété de la *solution bac à sable (sandbox* ) et que sa valeur est définie sur **true**, le débogueur est attaché à un processus différent (*SPUCWorkerProcess.exe*). Pour plus d’informations, consultez [Considérations sur les solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

11. Démarre le débogueur JavaScript si la solution SharePoint est une solution de batterie de serveurs.

12. Affiche la bibliothèque, la liste ou la page de site appropriée dans le navigateur Web.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d’État dans la fenêtre sortie une fois chaque tâche terminée. Si une tâche ne peut pas être terminée, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d’erreur dans la fenêtre Liste d’erreurs.

## <a name="sharepoint-project-features"></a>Fonctionnalités de projet SharePoint
 Une fonctionnalité est une unité de fonctionnalité portable et modulaire qui simplifie la modification de sites à l’aide de définitions de site. Il s’agit également d’un package d' [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] éléments (WSS) qui peuvent être activés pour une étendue spécifique et qui aide les utilisateurs à accomplir un objectif ou une tâche spécifique. Les modèles sont déployés en tant que fonctionnalités.

 Quand vous exécutez un projet en mode débogage, le processus de déploiement crée un dossier dans le répertoire de *fonctionnalités* à l’adresse *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Les noms de fonctionnalités ont le format *nom de projet* _Feature *x*, tel que TestProject_Feature1.

 Le dossier de la solution dans le répertoire des fonctionnalités contient un fichier de *définition de fonctionnalité* et un fichier de définition de *flux de travail* . Le fichier de définition de fonctionnalité (Feature.xml) décrit les fichiers dans la fonctionnalité du projet. le fichier de définition de projet (*Elements.xml*) décrit le modèle de projet. *Elements.xml* se trouve dans **Explorateur de solutions**, mais Feature.xml est générée lors de la création du package de solution. Pour plus d’informations sur ces fichiers, consultez [modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Déboguer des workflows
 Quand vous déboguez des projets de workflow, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le modèle de flux de travail (en fonction de son type) à une bibliothèque ou à une liste. Vous pouvez ensuite démarrer le modèle de flux de travail manuellement ou en ajoutant ou en mettant à jour un élément. Vous pouvez ensuite utiliser [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déboguer le flux de travail.

> [!NOTE]
> Si vous ajoutez des références à d’autres assemblys, assurez-vous que ces assemblys sont installés dans le Global Assembly Cache ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Dans le cas contraire, la solution de workflow échouera. Pour plus d’informations sur l’installation d’assemblys, consultez [démarrer manuellement un flux de travail sur un document ou un élément](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Toutefois, le processus de déploiement ne démarre pas le flux de travail. Vous devez démarrer le flux de travail à partir du site Web SharePoint. Vous pouvez également démarrer le flux de travail à l’aide d’une application cliente telle que Microsoft Office Word 2010 ou à l’aide d’un code distinct côté serveur. Utilisez l’une des approches spécifiées dans l' **Assistant Personnalisation de SharePoint**.

 Par exemple, si vous avez spécifié que le flux de travail peut être démarré manuellement, démarrez le flux de travail directement à partir de l’élément dans la bibliothèque ou la liste. Pour plus d’informations sur la façon de démarrer un flux de travail manuellement, consultez [démarrer manuellement un flux de travail sur un élément de document](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Déboguer les récepteurs d’événements de fonctionnalité
 Par défaut, lorsque vous exécutez une [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] application SharePoint, ses fonctionnalités sont automatiquement activées pour vous sur le serveur SharePoint. Toutefois, cela pose des problèmes lorsque vous déboguez des récepteurs d’événements de fonctionnalité, car lorsqu’une fonctionnalité est activée par [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , elle s’exécute dans un processus différent de celui du débogueur. Cela signifie que certaines fonctionnalités de débogage, telles que les points d’arrêt, ne fonctionneront pas correctement.

 Pour désactiver l’activation automatique de la fonctionnalité dans SharePoint et autoriser le débogage approprié des récepteurs d’événements de fonctionnalité, définissez la valeur de la propriété de **configuration de déploiement active** du projet sur **aucune activation** avant le débogage. Ensuite, une fois que vous avez commencé à déboguer votre application SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , activez manuellement la fonctionnalité dans SharePoint. Pour activer la fonctionnalité, ouvrez le menu **actions du site** dans SharePoint, choisissez Paramètres du **site**, cliquez sur le lien gérer les **fonctionnalités du site** , puis sélectionnez le bouton **activer** en regard de la fonctionnalité pour continuer le débogage normalement.

## <a name="enable-enhanced-debugging-information"></a>Activer les informations de débogage avancées
 En raison des interactions parfois complexes entre le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processus (devenv.exe), le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processus hôte sharepoint (*vssphost4.exe*), SharePoint et la couche WCF, le diagnostic des erreurs qui se produisent pendant la génération, le déploiement et ainsi de suite peut être un défi. Pour vous aider à résoudre ces erreurs, vous pouvez activer des informations de débogage avancées. Pour ce faire, accédez à la clé de Registre suivante dans le Registre Windows :

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Si la valeur « EnableDiagnostics » **REG_DWORD** n’existe pas encore, créez-la manuellement. Définissez la valeur « EnableDiagnostics » sur « 1 ».

 Si vous affectez la valeur 1 à cette valeur de clé, les informations de trace de la pile s’affichent dans la fenêtre **sortie** à chaque fois que des erreurs système du projet se produisent pendant l’exécution de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour désactiver les informations de débogage avancées, affectez à EnableDiagnostics la valeur 0 ou supprimez la valeur.

 Pour plus d’informations sur les autres clés de Registre SharePoint, consultez [extensions de débogage pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Résoudre les problèmes des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)

---
title: Débogage de Solutions SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60aa38d5042625393132ffceb3cc226f44e67645
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443487"
---
# <a name="debug-sharepoint-solutions"></a>Déboguer des solutions SharePoint
  Vous pouvez déboguer des solutions SharePoint à l’aide de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] débogueur. Lorsque vous démarrez le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] déploie les fichiers de projet sur le serveur SharePoint, puis ouvre une instance du site SharePoint dans le navigateur Web. Les sections suivantes expliquent comment déboguer des applications SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Activer le débogage](#enable-debugging)

- [Processus de débogage et de déploiement F5](#f5-debug-and-deployment-process)

- [Fonctionnalités de projet SharePoint](#sharepoint-project-features)

- [Déboguer des workflows](#debug-workflows)

- [Déboguer les récepteurs d’événements de fonctionnalité](#debug-feature-event-receivers)

- [Activer les informations de débogage d’ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Activer le débogage
 Lorsque vous déboguez tout d’abord une solution SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], une boîte de dialogue vous avertit que le fichier web.config n’est pas configuré pour activer le débogage. (Le fichier web.config est créé lorsque vous installez SharePoint server. Pour plus d’informations, consultez [utilisation des fichiers Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) La boîte de dialogue vous donne la possibilité d’exécution du projet sans débogage ou en modifiant le fichier web.config pour activer le débogage. Si vous choisissez la première option, le projet s’exécute normalement. Si vous choisissez la deuxième option, le fichier web.config est configuré pour :

- Activer la pile des appels (`CallStack="true"`)

- Désactiver les erreurs personnalisées dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- Activer le débogage de compilation (`<compilation debug="true">`)

  Le fichier web.config suivant :

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

 Pour annuler les modifications et désactiver le débogage, modifier les paramètres suivants [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dans le fichier web.config :

- Désactiver la pile des appels (`CallStack="false"`)

- Activer les erreurs personnalisées en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

- Désactiver le débogage de compilation (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>Processus de débogage et de déploiement F5
 Lorsque vous exécutez votre projet SharePoint en mode débogage, le processus de déploiement SharePoint effectue les tâches suivantes :

1. Exécute les commandes de prédéploiement personnalisables.

2. Crée un fichier de package (.wsp) solution Web à l’aide de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] commandes. Le fichier .wsp inclut tous les fichiers nécessaires et les fonctionnalités. Pour plus d’informations, consultez [vue d’ensemble des Solutions](http://go.microsoft.com/fwlink/?LinkID=128154).

3. Si la solution SharePoint est une solution de batterie, il recycle le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool d’applications pour le site spécifié [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Cette étape libère des fichiers verrouillés par le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processus de travail.

4. Si une version antérieure du package existe déjà, retire la version précédente des fonctionnalités et des fichiers dans le fichier .wsp. Cette étape désactive les fonctionnalités, désinstalle le package de solution, puis supprime le package de solution sur le serveur SharePoint.

5. Installe la version actuelle des fonctionnalités et des fichiers dans le fichier .wsp. Cette étape ajoute et installe la solution sur le serveur SharePoint.

6. Pour les flux de travail, installe l’assembly de flux de travail. Vous pouvez modifier son emplacement en utilisant le *emplacement de l’Assembly* propriété.

7. Active la fonctionnalité du projet dans SharePoint si l’étendue est le Site ou Web. Fonctionnalités dans les étendues de la batterie de serveurs et WebApplication ne sont pas activées.

8. Pour les workflows, associe le flux de travail à la bibliothèque SharePoint, liste ou le site que vous avez sélectionné dans le **Assistant Personnalisation de SharePoint**.

   > [!NOTE]
   > Cette association se produit uniquement si vous avez sélectionné **workflow associer automatiquement** dans l’Assistant.

9. Exécute les commandes de post-déploiement personnalisables.

10. Attache le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] du débogueur pour le [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] processus (*w3wp.exe*). Si le type de projet vous permet de modifier le *Solution bac à sable* propriété et sa valeur est définie sur **true**, le débogueur est joint à un autre processus (*SPUCWorkerProcess.exe*). Pour plus d’informations, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).

11. Démarre le débogueur JavaScript si la solution SharePoint est une solution de batterie de serveurs.

12. Affiche la bibliothèque appropriée, une liste ou une page de site dans le navigateur Web.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d’état dans la fenêtre sortie après que chaque tâche est terminée. Si une tâche ne peut pas être effectuée, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] affiche un message d’erreur dans la fenêtre liste d’erreurs.

## <a name="sharepoint-project-features"></a>Fonctionnalités de projet SharePoint
 Une fonctionnalité est une unité portable et modulaire de fonctionnalités qui simplifient la modification des sites à l’aide de définitions de site. Il existe également un package de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] éléments (WSS) qui peuvent être activés pour une portée spécifique et qui permet aux utilisateurs de réaliser une tâche ou un objectif particulier. Les modèles sont déployés en tant que fonctionnalités.

 Lorsque vous exécutez un projet en mode débogage, le processus de déploiement crée un dossier dans le *fonctionnalité* répertoire à *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Les noms de fonction présentent le format *nom_projet*_fonctionnalités de le*x*, tels que TestProject_Feature1.

 Dossier de la solution dans le répertoire des fonctionnalités contient un *la définition de fonctionnalité* fichier et un *définition de workflow* fichier. Le fichier de définition de fonctionnalité (Feature.xml) décrit les fichiers dans le fichier de définition de projet de fonction du projet (*Elements.xml*) décrit le modèle de projet. *Elements.XML* se trouve dans **l’Explorateur de solutions**, mais de Feature.xml est généré lorsque le package de solution est créé. Pour plus d’informations sur ces fichiers, consultez [SharePoint modèles d’élément de projet et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Déboguer des workflows
 Lorsque vous déboguez des projets de flux de travail, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le modèle de flux de travail (selon son type) dans une bibliothèque ou à une liste. Vous pouvez ensuite démarrer le modèle de flux de travail manuellement ou en ajoutant ou en mettant à jour un élément. Vous pouvez ensuite utiliser [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déboguer le flux de travail.

> [!NOTE]
> Si vous ajoutez des références à d’autres assemblys, assurez-vous que ces assemblys sont installés dans le global assembly cache ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Sinon, la solution de flux de travail risque d’échouer. Pour plus d’informations sur la façon d’installer des assemblys, consultez [démarrer manuellement un flux de travail sur un document ou un élément](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Toutefois, le processus de déploiement ne démarre pas le flux de travail. Vous devez démarrer le flux de travail à partir du site SharePoint Web. Vous pouvez également démarrer le flux de travail à l’aide d’une application cliente comme Microsoft Office Word 2010 ou à l’aide de code côté serveur distinct. Utilisez une des approches indiquées dans le **Assistant Personnalisation de SharePoint**.

 Par exemple, si vous avez spécifié que le flux de travail peut être démarré manuellement, vous pouvez démarrer le flux de travail directement à partir de l’élément dans la liste ou bibliothèque. Pour plus d’informations sur la façon de démarrer un flux de travail manuellement, consultez [démarrer manuellement un flux de travail sur un élément de document](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Déboguer les récepteurs d’événements de fonctionnalité
 Par défaut, lorsque vous exécutez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] application SharePoint, ses fonctionnalités sont automatiquement activées sur le serveur SharePoint. Toutefois, cela pose des problèmes lorsque vous déboguez des récepteurs d’événements, car lorsque la fonctionnalité est activée par [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elle s’exécute dans un processus autre que le débogueur. Cela signifie que certaines fonctionnalités de débogage, telles que des points d’arrêt, ne fonctionnera pas correctement.

 Pour désactiver l’activation automatique de la fonctionnalité dans SharePoint et permettre un débogage approprié des récepteurs d’événements de fonctionnalité, affectez la valeur du projet **Configuration de déploiement Active** propriété **aucune Activation** avant le débogage. Ensuite, une fois que vous commencez à déboguer votre application SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]manuellement activer la fonctionnalité dans SharePoint. Pour activer la fonctionnalité, ouvrez le **Actions du Site** menu dans SharePoint, choisissez **paramètres du Site**, choisissez le **gérer les fonctionnalités du Site** lier, puis choisissez le **Activer** bouton en regard de la fonctionnalité pour continuer le débogage comme d’habitude.

## <a name="enable-enhanced-debugging-information"></a>Activer les informations de débogage avancées
 En raison des interactions parfois complexes entre la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processus (devenv.exe), le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processus hôte SharePoint (*vssphost4.exe*), SharePoint et la couche WCF, diagnostiquer les erreurs qui se produisent alors que génération, déploiement et ainsi de suite peuvent être un défi. Pour vous aider à résoudre ces erreurs, vous pouvez activer les informations de débogage avancées. Pour ce faire, accédez à la clé de Registre suivante dans le Registre Windows :

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Si le « EnableDiagnostics » **REG_DWORD** valeur n’existe pas déjà, la créer manuellement. Définissez la valeur « EnableDiagnostics » à « 1 ».

 La valeur clé 1 causes stack trace des informations apparaissent dans le **sortie** fenêtre chaque fois que les erreurs de système de projet se produisent pendant l’exécution [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour désactiver les informations de débogage avancé, définissez EnableDiagnostics à 0, ou supprimer la valeur.

 Pour plus d’informations sur les autres clés de Registre SharePoint, consultez [déboguer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Résoudre les problèmes des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)

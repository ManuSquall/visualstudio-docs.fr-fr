---
title: Empaquetage et déploiement de solutions SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45815e03d887f4d22f2559acf741f612cab34c49
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986204"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Empaqueter et déployer des solutions SharePoint
  En règle générale, une solution SharePoint est déployée sur un serveur SharePoint à l’aide d’un fichier de package de solution (. wsp). Vous pouvez utiliser Visual Studio pour organiser vos éléments de projet SharePoint en fonctionnalités et créer un package pour déployer vos fonctionnalités SharePoint.

 Cette rubrique fournit les informations suivantes :

- [Créer des fonctionnalités et des packages](#create-features-and-packages)

- [Prise en charge des outils de fonctionnalité et d’empaquetage](#feature-and-packaging-tool-support)

- [Déployer des solutions SharePoint](#deploy-sharepoint-solutions)

- [Déployer des fichiers dans des solutions SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Créer des fonctionnalités et des packages
 Vous pouvez utiliser Visual Studio pour regrouper des éléments SharePoint connexes dans une *fonctionnalité*. Par exemple, une fonctionnalité pour une définition de liste de contacts peut inclure l’instance de liste et la définition de liste. Vous pouvez combiner ces deux éléments en une seule fonctionnalité à des fins de déploiement. Pour plus d’informations sur les fonctionnalités, consultez [bloc de construction : fonctionnalités](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Ensuite, vous pouvez créer un package de solution SharePoint ( *. wsp*) pour regrouper plusieurs fonctionnalités, définitions de site, assemblys et autres fichiers dans un package unique, qui stocke les fichiers dans un format requis par SharePoint pour déployer les fichiers sur le serveur. Pour plus d’informations, consultez [bloc de construction : solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Prise en charge des outils de fonctionnalité et d’empaquetage
 Vous pouvez utiliser les outils de développement SharePoint dans Visual Studio pour organiser rapidement vos fichiers SharePoint en fonctionnalités et packages de solutions pour faciliter le déploiement. Vous pouvez utiliser les outils suivants pour configurer la fonctionnalité et le package de solution.

- Concepteur de fonctionnalités et concepteur de packages.

- L’Explorateur de package, une fenêtre outil.

- Explorateur de solutions.

### <a name="feature-designer-and-package-designer"></a>Concepteur de fonctionnalités et concepteur de packages
 Vous pouvez créer des fonctionnalités, définir des étendues et marquer d’autres fonctionnalités en tant que dépendances à l’aide du concepteur de fonctionnalités. Le concepteur affiche également le fichier XML final qui décrit chaque fonctionnalité. Pour plus d’informations, consultez [créer des fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md).

 Appliquez la fonctionnalité à un site Web spécifique ou à un groupe de sites Web en définissant son *étendue* dans le concepteur de fonctionnalités. Si une fonctionnalité est activée pour un site Web individuel, la fonctionnalité ne fonctionne que dans ce site Web particulier. Si une fonctionnalité est activée pour une collection de sites, les éléments de la fonctionnalité s’appliquent à l’ensemble de la collection de sites. Pour plus d’informations, consultez [portée des éléments](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Si votre fonctionnalité s’appuie sur d’autres fonctionnalités, vous pouvez définir une *dépendance d’activation de fonctionnalité* pour marquer les fonctionnalités dépendantes avant de rendre votre fonctionnalité disponible. Une dépendance d’activation de fonctionnalité vérifie si les fonctionnalités dépendantes sont déjà activées dans cette étendue. Pour plus d’informations, consultez [dépendances d’activation et portée](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 Dans le concepteur de packages, vous pouvez regrouper des éléments SharePoint dans un package de solution unique et configurer si le serveur Web doit être réinitialisé lors du déploiement. Pour définir le type de serveur de déploiement, utilisez la fenêtre **Propriétés** . Le concepteur génère également le fichier XML qui décrit le contenu du package. Pour plus d’informations, consultez [créer des packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Pendant le déploiement, le service Internet Information Services (IIS) est arrêté pour copier les fichiers de solution sur le serveur SharePoint. À l’aide du concepteur de packages dans Visual Studio, vous pouvez choisir si le serveur Web doit être redémarré. Pour configurer si la solution est déployée sur un serveur Web frontal ou un serveur d’applications, utilisez la fenêtre **Propriétés** . Pour plus d’informations, consultez [solution, élément (solution)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Explorateur de package
 Pour compléter le concepteur de fonctionnalités et le concepteur de packages, vous pouvez utiliser l’Explorateur de packages pour regrouper vos fichiers SharePoint en fonctionnalités et packages. En outre, vous pouvez voir la vue hiérarchique du package, des fonctionnalités, des éléments de projet SharePoint et des fichiers. L’Explorateur de package est une fenêtre outil que vous pouvez utiliser pour effectuer les tâches suivantes :

- Ouvrir les éléments de projet et les fichiers SharePoint.

- Glisser-déplacer des éléments de projet SharePoint d’une fonctionnalité à une autre.

- Glisser-déplacer des éléments et des fonctionnalités de projet SharePoint d’un package vers un autre.

- Ajoutez une nouvelle fonctionnalité à un package.

- Ouvrez un concepteur de fonctionnalités ou de packages.

- Validez les fonctionnalités et les packages.

  Les outils de développement SharePoint dans Visual Studio ont des règles de validation pour vous aider à garantir que le package de solution est correctement formé. En outre, les règles vérifient que le fichier solution *. wsp* peut être déployé et activé avec succès sur un serveur SharePoint. Pour plus d’informations sur le schéma XML des fonctionnalités, consultez [schémas de fonctionnalités](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Vous pouvez ajouter des règles de validation de fonctionnalité et de package personnalisées au système de projet SharePoint. Pour plus d’informations, consultez [Comment : créer des règles de validation de fonctionnalité et de package personnalisées pour les solutions SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Pour plus d’informations sur l’Explorateur de packages, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide de l’Explorateur](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)de package.

### <a name="solution-explorer"></a>l'Explorateur de solutions
 Vous pouvez utiliser Explorateur de solutions pour naviguer et ouvrir les fichiers du projet SharePoint. Utilisez le menu contextuel de Explorateur de solutions pour ajouter des fonctionnalités, des récepteurs d’événements de fonctionnalité et des ressources de fonctionnalités. En outre, vous pouvez ouvrir les concepteurs de fonctionnalités et les concepteurs de packages pour configurer les fonctionnalités et les packages à déployer.

## <a name="deploy-sharepoint-solutions"></a>Déployer des solutions SharePoint
 Une fois que vous avez personnalisé les fonctionnalités et le package dans Visual Studio, vous pouvez créer un fichier *. wsp* à déployer sur les serveurs SharePoint. Vous pouvez utiliser Visual Studio pour déboguer et tester le. *wsp* uniquement sur le serveur SharePoint sur l’ordinateur de développement. Pour plus d’informations sur le déploiement de vos solutions SharePoint sur un serveur SharePoint distant, consultez [déploiement d’une solution](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Vous pouvez également personnaliser les étapes de déploiement sur l’ordinateur de développement. Pour plus d’informations, consultez [déployer, publier et mettre à niveau des packages de solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Déployer des fichiers dans des solutions SharePoint
 En règle générale, lorsque vous ajoutez un élément de projet SharePoint à votre solution SharePoint, tous les fichiers requis sont inclus. Les fichiers qui peuvent être compilés (fichiers de code) sont intégrés à l’assembly de sortie de la solution. Toutefois, vous devrez peut-être également ajouter des fichiers non compilables, par exemple *. xml*, *. txt*ou des fichiers de ressources, à un projet SharePoint. Ces fichiers ne sont pas automatiquement empaquetés dans votre solution. Pour vous assurer qu’ils sont empaquetés, ajoutez les fichiers à un dossier mappé ou à un élément de projet SharePoint.

 Les fichiers ajoutés aux dossiers mappés sont automatiquement copiés dans la ruche SharePoint lorsque la solution est déployée. Les fichiers ajoutés à un élément de projet SharePoint sont déployés à l’emplacement spécifié dans la propriété **emplacement de déploiement** pour chaque fichier, qui est partiellement défini en fonction de la propriété **type de déploiement** . Par défaut, la valeur de la propriété **type de déploiement** est **NoDeployment**, ce qui signifie que le fichier n’est pas déployé avec la solution. Vous devez définir une autre valeur pour la propriété afin d’inclure le fichier dans le package.

 Par exemple, pour ajouter un fichier *. xml* à un projet SharePoint, effectuez l’une des actions suivantes :

- Ajoutez un dossier mappé « dispositions » SharePoint à votre projet. Cela crée dans **Explorateur de solutions** un dossier nommé **dispositions** qui a un sous-dossier pour le projet. Ajoutez le fichier *. xml* au nouveau sous-dossier. Par défaut, le fichier est déployé dans le système de fichiers SharePoint sous *. \TEMPLATE\LAYOUTS\\\<nom du dossier >* . Pour plus d’informations sur l’ajout de dossiers mappés, consultez [procédure : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Ajoutez le fichier *. xml* au dossier d’un élément de projet SharePoint, puis modifiez la propriété **type de déploiement** du fichier *. xml* de **NoDeployment** en un autre paramètre, tel que **RootFile** ou **ElementFile**. Le paramètre de **type de déploiement** approprié dépend du fichier et du projet. Pour plus d’informations sur les paramètres de propriété du **type de déploiement** , consultez [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Si un fichier ajouté ne s’applique à aucun projet spécifique dans la solution, vous pouvez ajouter un projet SharePoint vide à votre solution, puis y ajouter les fichiers supplémentaires. Une autre solution pour déployer des fichiers sur SharePoint, en particulier sur la base de données de contenu, consiste à ajouter un module au projet, puis à ajouter les fichiers au module. Pour plus d’informations, consultez [utiliser des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)

---
title: Conception d’un modèle de connectivité de données métiers | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f322d18afdb8e14ee87ae31d30dd6bdd57b07c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431283"
---
# <a name="design-a-business-data-connectivity-model"></a>Concevoir un modèle de connectivité de données métiers
  Vous pouvez développer un modèle pour le service de connectivité de données métiers (BDC) en ajoutant des entités et des méthodes à un fichier de modèle. Une entité décrit une collection de champs de données. Par exemple, une entité peut représenter une table dans une base de données. Une méthode effectue une tâche comme l’ajout, suppression ou la mise à jour des données représentées par les entités. Pour plus d’informations, consultez [intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Ajouter des entités
 Vous pouvez ajouter une entité en faisant glisser ou en copiant un **entité** à partir de Visual Studio **boîte à outils** sur le concepteur BDC. Pour plus d'informations, voir [Procédure : Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Définissez les champs de l’entité dans une classe. Par exemple, vous pouvez ajouter un champ nommé `Address` à un `Customer` classe. Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à l’aide d’autres outils tels que le Concepteur Objet/Relationnel (Concepteur O/R). Le nom de l’entité et le nom de la classe qui représente l’entité n’ont pas faire correspondre. Vous liez la classe à l’entité lorsque vous définissez les méthodes dans votre modèle.

## <a name="add-methods"></a>Ajouter des méthodes
 Le service BDC appelle des méthodes dans votre modèle lorsque les utilisateurs à afficher, ajoutent, mettre à jour ou supprimer les informations dans une liste ou un composant WebPart qui est basé sur votre modèle. Vous devez ajouter une méthode au modèle pour chaque tâche que l’utilisateur peut effectuer. Créer des méthodes en sélectionnant une des cinq types de méthode de base à partir de la **détails de méthode BDC** fenêtre. Le tableau suivant décrit les cinq méthodes de base d’un modèle BDC.

|Méthode|Description|
|------------|-----------------|
|Finder|Retourne une collection d’instances d’entité. Appelée lorsque l’utilisateur ouvre la liste ou un composant WebPart. Pour plus d'informations, voir [Procédure : Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md).|
|recherche spécifique|Retourne une instance d’entité spécifique. Appelé lorsqu’un utilisateur affiche les détails d’un élément spécifique dans une liste. Pour plus d'informations, voir [Procédure : Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md).|
|créateur|Ajoute les nouvelles données à la source de données d’une entité. Appelé lorsque les utilisateurs choisissent le **un nouvel élément** bouton sur le ruban d’une liste qui est basée sur le modèle. Pour plus d'informations, voir [Procédure : Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md).|
|programme de mise à jour|Modifie les données dans une liste. Appelée lorsque les utilisateurs mettent à jour les informations dans une liste. Pour plus d'informations, voir [Procédure : Ajoutez une méthode de mise à jour du](../sharepoint/how-to-add-an-updater-method.md).|
|programme de suppression|Supprime les données. Appelée lorsque les utilisateurs suppriment un élément dans la liste. Pour plus d'informations, voir [Procédure : Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Définir les paramètres de méthode
 Lorsque vous créez une méthode, Visual Studio ajoute les paramètres d’entrée et de sortie qui sont appropriés pour le type de méthode. Ces paramètres sont seulement des espaces réservés. Dans la plupart des cas, vous devez modifier les paramètres afin qu’ils passent ou retournent le type de données approprié. Par exemple, par défaut, une méthode de recherche retourne une chaîne. Dans la plupart des cas, vous souhaitez modifier le paramètre de retour de la méthode de recherche afin qu’elle retourne une collection d’entités. Vous pouvez le faire en modifiant le descripteur de type du paramètre. Un descripteur de type est une collection d’attributs qui décrit le type de données d’un paramètre. Pour plus d'informations, voir [Procédure : Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio vous permet de copier des descripteurs de type entre les paramètres dans le modèle. Par exemple, vous pouvez définir un descripteur de type nommé `CustomerTD` pour le paramètre de retour de la `GetCustomer` (méthode). Vous pouvez copier le `CustomerTD` tapez descripteur dans la **Explorateur BDC**, puis collez ce descripteur de type pour le paramètre d’entrée de la `CreateCustomer` (méthode). Cela vous évite d’avoir à définir le même descripteur de type plusieurs fois.

## <a name="method-instances"></a>Instances (méthode)
 Lorsque vous créez une méthode, Visual Studio ajoute une instance de la méthode par défaut. Une instance de méthode est une référence à une méthode, ainsi que les valeurs par défaut pour les paramètres. Une méthode unique peut avoir plusieurs instances de méthode. Chaque instance est une combinaison de la signature de méthode et un ensemble de valeurs par défaut. Pour plus d'informations, voir [Procédure : Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Lorsque vous exécutez le projet, les instances de la méthode figurent dans une liste déroulante au-dessus de la liste SharePoint. Les utilisateurs peuvent choisir des instances de méthode pour afficher les données.

 Pour ajouter des valeurs par défaut à l’instance de méthode, vous devez modifier le code XML du modèle directement. Pour plus d’informations, consultez [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).

## <a name="add-filter-descriptors"></a>Ajouter des descripteurs de filtre
 Les consommateurs du modèle peuvent souhaiter récupérer les instances d’une entité qui correspondent à certains critères. Pour activer cette fonctionnalité, vous pouvez ajouter un descripteur de filtre à une méthode. Descripteurs de filtre permettent aux consommateurs de modèle filtrer les jeux de résultats de méthode en passant des valeurs aux méthodes avant leur exécution. Pour plus d'informations, voir [Procédure : Ajouter des paramètres de filtre pour limiter les Instances du système externe de](http://go.microsoft.com/fwlink/?LinkID=169267).

 SharePoint fournit plusieurs fonctionnalités qui permettent aux utilisateurs de fournir des valeurs de filtre. Par exemple, les composants WebPart de données de l’entreprise fournissent une zone de texte de filtre. Les utilisateurs peuvent limiter les données dans une liste en entrant une valeur dans la zone de texte. Pour plus d’informations sur l’ajout d’un descripteur de filtre à une méthode, consultez [Comment : Ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Propriétés du descripteur de filtre
 Vous devez définir la valeur de la **descripteurs de Type associés**, **nom**, et **Type** propriétés d’un descripteur de filtre. Toutes les autres propriétés sont facultatives.

 Le **descripteurs de Type associés** propriété concerne le descripteur de filtre à un paramètre d’entrée. Lorsqu’un utilisateur fournit une valeur de filtre, le service BDC passe cette valeur dans la méthode en utilisant le paramètre d’entrée.

 Le **Type** propriété décrit le modèle de filtrage que vous souhaitez utiliser. Dans SharePoint, le modèle de filtrage que vous sélectionnez affecte le texte qui apparaît dans l’Interface utilisateur (IU). Par exemple, pour un modèle de filtrage comparateur, le texte **est égal à** apparaît sous la forme d’un contrôle situé au-dessus d’un composant WebPart données métier. Pour plus d’informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le BDC](http://go.microsoft.com/fwlink/?LinkId=169287).

 Pour plus d’informations sur les propriétés d’un descripteur de filtre, consultez [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).

### <a name="provide-default-values"></a>Fournir des valeurs par défaut
 Dans certains cas, l’utilisateur peut ne pas fournit une valeur de filtre. Vous pouvez fournir une valeur par défaut en ajoutant une valeur par défaut à l’instance de méthode, ou en définissant la valeur par défaut dans le code de votre méthode. Pour plus d’informations sur l’ajout d’une valeur par défaut à l’instance de méthode, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Pour obtenir un exemple montrant comment définir la valeur par défaut d’un paramètre d’entrée dans le code de votre méthode, consultez [Comment : Ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Valider le modèle
 Vous pouvez valider votre modèle pendant le développement. Visual Studio identifie les problèmes qui peuvent empêcher votre modèle de se comporter comme prévu. Ces problèmes s’affichent dans Visual Studio **liste d’erreurs**.

 Vous pouvez valider un modèle en ouvrant le menu contextuel pour le concepteur BDC, puis en choisissant **Validate**. Si le modèle contient des erreurs, ils apparaissent dans le **liste d’erreurs**. Vous pouvez rapidement déplacer le curseur vers le code qui contient une erreur en double-cliquant sur l’erreur dans la liste. Comme alternative, vous pouvez choisir le **F8** ou **MAJ**+**F8** clés à plusieurs reprises pour avancer ou reculer dans les erreurs dans la liste.

 Erreurs de validation peuvent se produire lorsque les règles du modèle sont enfreintes d’une certaine façon. Par exemple, si le **IsCollection** propriété d’un descripteur de type est définie sur **true**, mais aucun descripteur de type enfant n’existe, une erreur de validation s’affiche. Vous devrez peut-être faire référence aux règles d’un modèle BDC pour comprendre certaines des erreurs qui s’affichent dans Visual Studio **liste d’erreurs**. Pour plus d’informations sur les règles d’un modèle BDC, consultez [BDCMetadata schéma](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="debug-the-solution-that-contains-the-model"></a>Déboguer la solution qui contient le modèle
 Vous pouvez déboguer votre code comme pour n’importe quel code dans Visual Studio. Pour déboguer votre code, définissez des points d’arrêt n’importe où dans votre code, puis démarrez le débogueur. Visual Studio ouvre le site SharePoint. Dans SharePoint, créez une liste ou un composant WebPart qui utilise vos données d’entreprise. Ensuite, vous pouvez parcourir votre code. Pour plus d’informations sur le débogage des projets SharePoint, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Vous pouvez également déboguer le code dans les assemblys personnalisés que vous ajoutez au projet. Toutefois, pour déboguer le code dans un assembly personnalisé, vous devez ajouter l’assembly pour le package de solution. Pour plus d'informations, voir [Procédure : Ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Pour plus d’informations sur l’ajout d’un assembly personnalisé à votre projet, consultez [Comment : Inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Configurer la sécurité BDC
 Il se peut que vous deviez modifier vos paramètres de sécurité dans SharePoint avant de pouvoir déboguer votre solution. Pour modifier ces paramètres, ouvrez l’Application de Service Business Data Connectivity sur le site Web de SharePoint 2010 Central Administration. Dans le **définir les autorisations de métadonnées Store** boîte de dialogue, ajoutez votre compte d’utilisateur, puis sélectionnez une des options suivantes :

|Tâche|Option|
|----------|------------|
|Pour déployer des modèles pour le service BDC.|Modifier|
|Pour créer des listes et composants WebPart à l’aide en externe des types de contenu (entités) dans votre modèle.|Sélectionnable dans les Clients|
|Pour créer, lire, mettre à jour et supprimer des données d’entité.|Exécuter|

 Pour plus d’informations sur ces paramètres, consultez [gestion de service Business Data Connectivity](http://go.microsoft.com/fwlink/?LinkID=178883).

 Vous pouvez également définir des autorisations de sécurité pour les modèles individuels ou des types de contenu externe. Pour plus d’informations sur la façon de définir les autorisations de sécurité d’un modèle, consultez [gestion des modèles BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Pour plus d’informations sur la façon de définir les autorisations de sécurité d’un type de contenu externe, consultez [gestion des types de contenu externe](http://go.microsoft.com/fwlink/?LinkID=178885).

> [!NOTE]
> Utilisez ces paramètres pour déboguer une solution sur votre serveur SharePoint local. Pour plus d’informations sur la configuration des paramètres de sécurité BDC sur le serveur de production SharePoint, consultez [vue d’ensemble de la sécurité Business Data Connectivity Services](http://go.microsoft.com/fwlink/?LinkID=178886).

### <a name="retract-models-that-become-corrupt"></a>Retrait des modèles corrompus
 La première fois que vous démarrez le débogueur, Visual Studio déploie le modèle entier sur SharePoint. Pour chaque fois par la suite, Visual Studio met à jour le modèle dans SharePoint avec les modifications que vous apportez entre les déploiements.

 Il peut exister des situations où vous souhaitez que Visual Studio pour retirer le modèle à partir de SharePoint complètement. Par exemple, un modèle peut être endommagé.  Pour redéployer votre modèle sur SharePoint, définissez le **mise à jour incrémentielle** propriété du modèle à **False**, puis démarrez le débogueur. Le **mise à jour incrémentielle** propriété s’affiche dans le **propriétés** fenêtre lorsque vous sélectionnez le nœud qui représente le modèle dans le **Explorateur BDC**. Par défaut, le nom du modèle est **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modifier les noms d’identificateurs d’entités dans le modèle
 Si vous modifiez le nom d’un identificateur après avoir déployé le modèle, vous pouvez recevoir une erreur de déploiement. Vous ne pouvez pas résoudre cette erreur en définissant le **mise à jour incrémentielle** propriété du modèle à **False**. Vous devez retirer le modèle manuellement et puis redéployez la solution. Pour plus d’informations, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md). Vous pouvez éviter cette erreur en définissant le **mise à jour incrémentielle** propriété **False** avant le déploiement initial du modèle.

## <a name="locate-documentation-for-bdc-model-elements"></a>Recherchez la documentation pour les éléments de modèle BDC
 Visual Studio ajoute un élément XML au modèle pour chaque entité, méthode ou un autre élément que vous créez. Attributs de l’élément s’affichent en tant que propriétés dans le **propriétés** fenêtre. Pour plus d’informations sur les éléments et attributs généré par Visual Studio lorsque vous concevez le modèle, consultez [BDCMetadata schéma](http://go.microsoft.com/fwlink/?LinkID=169275).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)|Décrit les outils que vous pouvez utiliser pour concevoir visuellement un modèle pour le BDC.|
|[Guide pratique pour Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)|Vous montre comment ajouter des types de contenu externe, ou des entités, au modèle.|
|[Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’afficher une liste d’entités dans une liste ou un composant WebPart.|
|[Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’afficher les détails d’une entité spécifique.|
|[Guide pratique pour Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’ajouter des enregistrements à une source de données directement à partir d’une liste ou un composant WebPart.|
|[Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs de supprimer des données à partir d’une source de données à l’aide des options dans l’Interface utilisateur (IU) d’une liste ou le composant WebPart.|
|[Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs de modifier des enregistrements de données dans une source de données directement à partir d’une liste ou un composant WebPart.|
|[Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Vous montre comment utiliser la fenêtre Détails de méthode dans Visual Studio pour ajouter des paramètres d’entrée et de retournés à une méthode.|
|[Guide pratique pour Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Vous montre comment définir des types de données de paramètre dans le modèle.|
|[Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)|Vous montre comment créer une instance d’une méthode qui exécute le BDC.|
|[Guide pratique pour Ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Vous montre comment permettre aux utilisateurs limiter le nombre d’instances retourné par une méthode de recherche.|
|[Création d’une association entre des entités](../sharepoint/creating-an-association-between-entities.md)|Décrit comment vous pouvez définir des relations entre les entités dans le modèle. Les composants WebPart de données de l’entreprise, des listes externes et des applications personnalisées peuvent afficher ces relations de données dans une interface utilisateur (IU).|
|[Guide pratique pour Créer une association entre entités](../sharepoint/how-to-create-an-association-between-entities.md)|Vous montre comment définir des relations entre des entités dans le modèle.|
|[Procédure pas à pas : Créer un liste externe dans SharePoint à l’aide des données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fournit des instructions pas à pas qui vous montrent comment créer et tester un modèle qui affiche les contacts dans une liste externe SharePoint.|
|[Intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Fournit une vue d’ensemble de la création et la conception de modèles pour le service BDC.|

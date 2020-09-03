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
ms.openlocfilehash: 16a410b59cef6f282d2d27ad90a90013636d6489
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72984463"
---
# <a name="design-a-business-data-connectivity-model"></a>Concevoir un modèle de connectivité de données métiers
  Vous pouvez développer un modèle pour le service de connectivité de données métiers (BDC) en ajoutant des entités et des méthodes à un fichier de modèle. Une entité décrit une collection de champs de données. Par exemple, une entité peut représenter une table dans une base de données. Une méthode effectue une tâche, telle que l’ajout, la suppression ou la mise à jour des données représentées par les entités. Pour plus d’informations, consultez [intégrer des données métier dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Ajouter des entités
 Vous pouvez ajouter une entité en faisant glisser ou en copiant une **entité** de la **boîte à outils** Visual Studio vers le concepteur BDC. Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Définissez les champs de l’entité dans une classe. Par exemple, vous pouvez ajouter un champ nommé `Address` à une `Customer` classe. Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à l’aide d’autres outils tels que le Concepteur Objet Relationnel (Concepteur O/R). Le nom de l’entité et le nom de la classe qui représente l’entité ne doivent pas nécessairement correspondre. Vous associez la classe à l’entité lorsque vous définissez les méthodes dans votre modèle.

## <a name="add-methods"></a>Ajouter des méthodes
 Le service BDC appelle des méthodes dans votre modèle lorsque les utilisateurs affichent, ajoutent, mettent à jour ou suppriment des informations dans une liste ou un composant WebPart basé sur votre modèle. Vous devez ajouter une méthode au modèle pour chaque tâche que l’utilisateur peut effectuer. Créez des méthodes en sélectionnant l’un des cinq types de méthode de base dans la fenêtre Détails de la **méthode BDC** . Le tableau suivant décrit les cinq méthodes de base d’un modèle BDC.

|Méthode|Description|
|------------|-----------------|
|Recherche|Retourne une collection d’instances d’entité. Appelé lorsque l’utilisateur ouvre la liste ou le composant WebPart. Pour plus d’informations, consultez [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md).|
|recherche spécifique|Retourne une instance d’entité spécifique. Appelée lorsqu’un utilisateur affiche les détails d’un élément spécifique dans une liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Creator|Ajoute de nouvelles données à la source de données d’une entité. Appelé lorsque les utilisateurs choisissent le bouton **nouvel élément** sur le ruban d’une liste basée sur le modèle. Pour plus d’informations, consultez [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md).|
|programme de mise à jour|Modifie les données d’une liste. Appelé lorsque les utilisateurs mettent à jour des informations dans une liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de](../sharepoint/how-to-add-an-updater-method.md)mise à jour.|
|programme de suppression|Supprime des données. Appelé lorsque les utilisateurs suppriment un élément de la liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Définir les paramètres de méthode
 Quand vous créez une méthode, Visual Studio ajoute les paramètres d’entrée et de sortie appropriés pour le type de méthode. Ces paramètres sont simplement des espaces réservés. Dans la plupart des cas, vous devez modifier les paramètres afin qu’ils passent ou retournent le type de données correct. Par exemple, une méthode Finder retourne une chaîne par défaut. Dans la plupart des cas, vous souhaitez modifier le paramètre de retour de la méthode Finder afin qu’il retourne une collection d’entités. Pour ce faire, vous pouvez modifier le descripteur de type du paramètre. Un descripteur de type est une collection d’attributs qui décrit le type de données d’un paramètre. Pour plus d’informations, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio vous permet de copier des descripteurs de type entre des paramètres dans le modèle. Par exemple, vous pouvez définir un descripteur de type nommé `CustomerTD` pour le paramètre de retour de la `GetCustomer` méthode. Vous pouvez copier le `CustomerTD` descripteur de type dans l' **Explorateur BDC**, puis coller ce descripteur de type dans le paramètre d’entrée de la `CreateCustomer` méthode. Cela vous empêche d’avoir à définir plusieurs fois le même descripteur de type.

## <a name="method-instances"></a>Instances de méthode
 Quand vous créez une méthode, Visual Studio ajoute une instance de méthode par défaut. Une instance de méthode est une référence à une méthode, plus les valeurs par défaut pour les paramètres. Une méthode unique peut avoir plusieurs instances de méthode. Chaque instance est une combinaison de la signature de la méthode et d’un ensemble de valeurs par défaut. Pour plus d’informations, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Lorsque vous exécutez le projet, les instances de méthode s’affichent dans une liste déroulante au-dessus de la liste SharePoint. Les utilisateurs peuvent choisir des instances de méthode pour afficher les données.

 Pour ajouter des valeurs par défaut à l’instance de méthode, vous devez modifier directement le XML du modèle. Pour plus d’informations, consultez [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Ajouter des descripteurs de filtre
 Les consommateurs du modèle peuvent souhaiter récupérer des instances d’une entité qui correspondent à certains critères. Pour activer cette fonctionnalité, vous pouvez ajouter un descripteur de filtre à une méthode. Les descripteurs de filtre permettent aux consommateurs de modèles de filtrer les jeux de résultats de méthode en passant des valeurs aux méthodes avant leur exécution. Pour plus d’informations, consultez [Comment : ajouter des paramètres de filtre à des opérations pour limiter les instances du système externe](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint fournit plusieurs fonctionnalités qui permettent aux utilisateurs de fournir des valeurs de filtre. Par exemple, les composants WebPart de données d’entreprise fournissent une zone de texte de filtre. Les utilisateurs peuvent limiter les données dans une liste en entrant une valeur dans la zone de texte. Pour plus d’informations sur l’ajout d’un descripteur de filtre à une méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Propriétés du descripteur de filtre
 Vous devez définir la valeur du **descripteur de type associé**, du **nom**et des propriétés de **type** d’un descripteur de filtre. Toutes les autres propriétés sont facultatives.

 La propriété du **descripteur de type associé** associe le descripteur de filtre à un paramètre d’entrée. Lorsqu’un utilisateur fournit une valeur de filtre, le service BDC transmet cette valeur à la méthode à l’aide du paramètre d’entrée.

 La propriété **type** décrit le modèle de filtrage que vous souhaitez utiliser. Dans SharePoint, le modèle de filtrage que vous sélectionnez affecte le texte qui apparaît dans l’interface utilisateur (IU). Par exemple, pour un modèle de filtrage de comparateur, le texte **est égal à** apparaît comme un contrôle au-dessus d’un composant WebPart de données métier. Pour plus d’informations sur chaque modèle de filtrage, consultez [types de filtres pris en charge par le CDM](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Pour plus d’informations sur les propriétés d’un descripteur de filtre, consultez [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Fournir les valeurs par défaut
 Dans certains cas, l’utilisateur peut ne pas fournir de valeur de filtre. Vous pouvez fournir une valeur par défaut en ajoutant une valeur par défaut à l’instance de méthode ou en définissant la valeur par défaut dans le code de votre méthode. Pour plus d’informations sur l’ajout d’une valeur par défaut à l’instance de méthode, consultez [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Pour obtenir un exemple de la façon de définir la valeur par défaut d’un paramètre d’entrée dans le code de votre méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Valider le modèle
 Vous pouvez valider votre modèle pendant le développement. Visual Studio identifie les problèmes qui peuvent empêcher votre modèle de se comporter comme prévu. Ces problèmes s’affichent dans le **liste d’erreurs**Visual Studio.

 Vous pouvez valider un modèle en ouvrant le menu contextuel du concepteur BDC, puis en choisissant **valider**. Si le modèle contient des erreurs, celles-ci apparaissent dans la **liste d’erreurs**. Vous pouvez rapidement déplacer le curseur vers le code qui contient une erreur en double-cliquant sur l’erreur dans la liste. Vous pouvez également choisir les touches **F8** ou **MAJ** + **F8** à plusieurs reprises pour effectuer un pas à pas détaillé ou reculer des erreurs dans la liste.

 Des erreurs de validation peuvent se produire lorsque les règles du modèle sont enfreintes d’une certaine manière. Par exemple, si la propriété **IsCollection** d’un descripteur de type a la valeur **true**, mais qu’il n’existe aucun descripteur de type enfant, une erreur de validation s’affiche. Vous devrez peut-être faire référence aux règles d’un modèle BDC pour comprendre certaines erreurs qui s’affichent dans le **liste d’erreurs**Visual Studio. Pour plus d’informations sur les règles d’un modèle BDC, consultez [schéma BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Déboguer la solution qui contient le modèle
 Vous pouvez déboguer votre code comme vous le feriez pour tout code dans Visual Studio. Pour déboguer votre code, définissez des points d’arrêt n’importe où dans votre code, puis démarrez le débogueur. Visual Studio ouvre le site SharePoint. Dans SharePoint, créez une liste ou un composant WebPart qui utilise vos données d’entreprise. Ensuite, vous pouvez parcourir votre code. Pour plus d’informations sur le débogage des projets SharePoint, consultez [résoudre les problèmes liés aux solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Vous pouvez également déboguer du code dans des assemblys personnalisés que vous ajoutez au projet. Toutefois, pour déboguer du code dans un assembly personnalisé, vous devez ajouter l’assembly au package de solution. Pour plus d’informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Pour plus d’informations sur l’ajout d’un assembly personnalisé à votre projet, consultez [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Configurer la sécurité BDC
 Vous devrez peut-être modifier vos paramètres de sécurité dans SharePoint pour pouvoir déboguer votre solution. Pour modifier ces paramètres, ouvrez l’application de service de connectivité de données métiers dans le site Web Administration centrale de SharePoint 2010. Dans la boîte de dialogue **définir les autorisations du magasin de métadonnées** , ajoutez votre compte d’utilisateur, puis sélectionnez l’une des options suivantes :

|Tâche|Option|
|----------|------------|
|Pour déployer des modèles dans le service BDC.|Modifier|
|Pour créer des listes et des composants WebPart à l’aide de types de contenu externes (entités) dans votre modèle.|Sélectionnable dans les clients|
|Pour créer, lire, mettre à jour et supprimer des données d’entité.|Execute|

 Pour plus d’informations sur ces paramètres, consultez [gestion des services Business Data Connectivity](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Vous pouvez également définir des autorisations de sécurité pour des modèles individuels ou des types de contenu externes. Pour plus d’informations sur la définition des autorisations de sécurité d’un modèle, consultez [gestion des modèles BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Pour plus d’informations sur la définition des autorisations de sécurité d’un type de contenu externe, consultez [gestion des types de contenu externes](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Utilisez ces paramètres pour déboguer une solution sur votre serveur SharePoint local. Pour plus d’informations sur la configuration des paramètres de sécurité liés à BDC sur le serveur SharePoint de production, consultez [vue d’ensemble de la sécurité de Business Data Connectivity Services](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Rétracter les modèles qui sont endommagés
 La première fois que vous démarrez le débogueur, Visual Studio déploie l’ensemble du modèle sur SharePoint. Pour chaque fois par la suite, Visual Studio met à jour le modèle dans SharePoint avec toutes les modifications que vous effectuez entre les déploiements.

 Il peut arriver que vous souhaitiez que Visual Studio rétracte complètement le modèle à partir de SharePoint. Par exemple, un modèle peut être endommagé.  Pour redéployer votre modèle dans SharePoint, affectez la valeur **false**à la propriété **mise à jour incrémentielle** du modèle, puis démarrez le débogueur. La propriété **mise à jour incrémentielle** s’affiche dans la fenêtre **Propriétés** de lorsque vous sélectionnez le nœud qui représente le modèle dans l' **Explorateur BDC**. Par défaut, le nom du modèle est **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modifier les noms d’identificateur des entités dans le modèle
 Si vous modifiez le nom d’un identificateur après avoir déployé le modèle, vous risquez de recevoir une erreur de déploiement. Vous ne pouvez pas résoudre cette erreur en affectant la **valeur false**à la propriété **mise à jour incrémentielle** du modèle. Vous devez retirer le modèle manuellement, puis déployer à nouveau la solution. Pour plus d’informations, consultez [résoudre les problèmes des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Vous pouvez éviter cette erreur en affectant à la propriété **mise à jour incrémentielle** la **valeur false** avant le déploiement initial du modèle.

## <a name="locate-documentation-for-bdc-model-elements"></a>Rechercher de la documentation pour les éléments de modèle BDC
 Visual Studio ajoute un élément XML au modèle pour chaque entité, méthode ou autre élément que vous créez. Les attributs d’élément apparaissent sous forme de propriétés dans la fenêtre **Propriétés** . Pour plus d’informations sur les éléments et attributs générés par Visual Studio au fur et à mesure que vous concevez le modèle, consultez [schéma BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)|Décrit les outils que vous pouvez utiliser pour concevoir visuellement un modèle pour le BDC.|
|[Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)|Montre comment ajouter des types de contenu externes ou des entités au modèle.|
|[Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)|Montre comment ajouter une méthode qui permet aux utilisateurs d’afficher une liste d’entités dans une liste ou un composant WebPart.|
|[Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)|Montre comment ajouter une méthode qui permet aux utilisateurs d’afficher les détails d’une entité spécifique.|
|[Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)|Montre comment ajouter une méthode qui permet aux utilisateurs d’ajouter des enregistrements à une source de données directement à partir d’une liste ou d’un composant WebPart.|
|[Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)|Montre comment ajouter une méthode qui permet aux utilisateurs de supprimer des données d’une source de données à l’aide des options de l’interface utilisateur d’une liste ou d’un composant WebPart.|
|[Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)|Montre comment ajouter une méthode qui permet aux utilisateurs de modifier des enregistrements de données dans une source de données directement à partir d’une liste ou d’un composant WebPart.|
|[Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Montre comment utiliser la fenêtre Détails de méthode dans Visual Studio pour ajouter des paramètres d’entrée et de retour à une méthode.|
|[Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Montre comment définir des types de données de paramètre dans le modèle.|
|[Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)|Montre comment créer une instance d’une méthode exécutée par le BDC.|
|[Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Montre comment permettre aux utilisateurs de limiter le nombre d’instances retournées par une méthode de recherche.|
|[Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md)|Décrit comment vous pouvez définir des relations entre des entités dans le modèle. Les composants WebPart de données métiers, les listes externes et les applications personnalisées peuvent afficher ces relations de données dans une interface utilisateur (IU).|
|[Comment : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md)|Montre comment définir des relations entre des entités dans le modèle.|
|[Procédure pas à pas : Createan liste externe dans SharePoint à l’aide de données d’entreprise](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fournit des instructions pas à pas qui vous montrent comment créer et tester un modèle qui affiche des contacts dans une liste externe SharePoint.|
|[Intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Fournit une vue d’ensemble de la création et de la conception de modèles pour le service BDC.|

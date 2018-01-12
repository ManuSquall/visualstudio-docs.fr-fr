---
title: "Conception d’un modèle de connectivité de données métiers | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe3de196219091478a30ff07d6c2f5916d423f15
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="designing-a-business-data-connectivity-model"></a>Conception d'un modèle de connectivité de données métiers
  Vous pouvez développer un modèle pour le service de connectivité de données métiers (BDC) en ajoutant des entités et des méthodes à un fichier de modèle. Une entité décrit une collection de champs de données. Par exemple, une entité peut représenter une table dans une base de données. Une méthode effectue une tâche telle que l’ajout, la suppression ou la mise à jour des données représentées par les entités. Pour plus d’informations, consultez [intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="adding-entities"></a>Ajout d’entités  
 Vous pouvez ajouter une entité en faisant glisser ou en copiant un **entité** à partir de Visual Studio **boîte à outils** sur le concepteur BDC. Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Définissez les champs de l’entité dans une classe. Par exemple, vous pouvez ajouter un champ nommé `Address` à un `Customer` classe. Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à l’aide d’autres outils tels que le Concepteur Objet/Relationnel (Concepteur O/R). Le nom de l’entité et le nom de la classe qui représente l’entité n’ont pas faire correspondre. Vous liez la classe à l’entité lorsque vous définissez les méthodes dans votre modèle.  
  
## <a name="adding-methods"></a>Ajout de méthodes  
 Le service BDC appelle des méthodes dans votre modèle lorsque les utilisateurs à afficher, ajoutent, mettre à jour ou supprimer des informations dans une liste ou un composant WebPart qui est basé sur votre modèle. Vous devez ajouter une méthode au modèle pour chaque tâche de l’utilisateur peut effectuer. Créer des méthodes en sélectionnant une des cinq types de méthode de base à partir de la **détails de méthode BDC** fenêtre. Le tableau suivant décrit les cinq méthodes de base d’un modèle BDC.  
  
|Méthode|Description|  
|------------|-----------------|  
|Finder|Retourne une collection d’instances d’entité. Appelé lorsque l’utilisateur ouvre la liste ou un composant WebPart. Pour plus d’informations, consultez [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md).|  
|recherche spécifique|Retourne une instance d’entité spécifique. Appelé lorsqu’un utilisateur affiche les détails d’un élément spécifique dans une liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|créateur|Ajoute de nouvelles données à la source de données d’une entité. Appelé lorsque les utilisateurs choisissent le **un nouvel élément** bouton sur le ruban d’une liste qui est basée sur le modèle. Pour plus d’informations, consultez [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md).|  
|programme de mise à jour|Modifie les données dans une liste. Appelé lorsque les utilisateurs mettent à jour les informations dans une liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md).|  
|programme de suppression|Supprime les données. Appelé lorsque les utilisateurs suppriment un élément dans la liste. Pour plus d’informations, consultez [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="defining-method-parameters"></a>Définition des paramètres de méthode  
 Lorsque vous créez une méthode, Visual Studio ajoute les paramètres d’entrée et de sortie qui sont appropriés pour le type de méthode. Ces paramètres sont seulement des espaces réservés. Dans la plupart des cas, vous devez modifier les paramètres afin qu’ils passent ou retournent le type de données approprié. Par exemple, par défaut, une méthode de recherche retourne une chaîne. Dans la plupart des cas, vous souhaitez modifier le paramètre de retour de la méthode de recherche afin qu’elle retourne une collection d’entités. Vous pouvez accomplir cela en modifiant le descripteur de type du paramètre. Un descripteur de type est une collection d’attributs qui décrit le type de données d’un paramètre. Pour plus d’informations, consultez [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio vous permet de copier des descripteurs de type entre les paramètres dans le modèle. Par exemple, vous pouvez définir un descripteur de type nommé `CustomerTD` pour le paramètre de retour de la `GetCustomer` (méthode). Vous pouvez copier le `CustomerTD` tapez descripteur dans le **Explorateur BDC**, puis collez ce descripteur de type pour le paramètre d’entrée de la `CreateCustomer` (méthode). Cela vous évite d’avoir à définir le même descripteur de type plusieurs fois.  
  
##  <a name="MethodInstances"></a>Instances (méthode)  
 Lorsque vous créez une méthode, Visual Studio ajoute une instance de la méthode par défaut. Une instance de méthode est une référence à une méthode, ainsi que les valeurs par défaut pour les paramètres. Une méthode unique peut avoir plusieurs instances de méthode. Chaque instance est une combinaison de la signature de méthode et un ensemble de valeurs par défaut. Pour plus d’informations, consultez [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Lorsque vous exécutez le projet, les instances de méthode s’affichent dans une liste déroulante au-dessus de la liste SharePoint. Les utilisateurs peuvent choisir des instances de méthode pour afficher les données.  
  
 Pour ajouter des valeurs par défaut à l’instance de méthode, vous devez modifier le code XML du modèle directement. Pour plus d’informations, consultez [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="adding-filter-descriptors"></a>Ajout de descripteurs de filtre  
 Les consommateurs du modèle peuvent souhaiter extraire les instances d’une entité qui correspondent à certains critères. Pour activer cette fonctionnalité, vous pouvez ajouter un descripteur de filtre à une méthode. Descripteurs de filtre permettent aux consommateurs de modèle filtrer les jeux de résultats de méthode en passant des valeurs aux méthodes avant leur exécution. Pour plus d’informations, consultez [Comment : ajouter des paramètres de filtre aux opérations pour limiter les Instances du système externe](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint fournit plusieurs fonctionnalités qui permettent aux utilisateurs de fournir des valeurs de filtre. Par exemple, les composants WebPart de données de l’entreprise fournissent une zone de texte de filtre. Les utilisateurs peuvent limiter les données dans une liste en entrant une valeur dans la zone de texte. Pour plus d’informations sur l’ajout d’un descripteur de filtre à une méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Propriétés du descripteur de filtre  
 Vous devez définir la valeur de la **descripteurs de Type associés**, **nom**, et **Type** propriétés d’un descripteur de filtre. Toutes les autres propriétés sont facultatives.  
  
 Le **descripteurs de Type associés** propriété concerne le descripteur de filtre à un paramètre d’entrée. Lorsqu’un utilisateur fournit une valeur de filtre, le service BDC passe cette valeur dans la méthode en utilisant le paramètre d’entrée.  
  
 Le **Type** propriété décrit le modèle de filtrage que vous souhaitez utiliser. Dans SharePoint, le modèle de filtrage que vous sélectionnez affecte le texte qui apparaît dans l’Interface utilisateur (IU). Par exemple, pour un modèle de filtrage comparateur, le texte **est égal à** apparaît sous la forme d’un contrôle au-dessus d’un composant WebPart données métier. Pour plus d’informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le catalogue de données métiers](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Pour plus d’informations sur les propriétés d’un descripteur de filtre, consultez [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="providing-default-values"></a>En fournissant des valeurs par défaut  
 Dans certains cas, l’utilisateur peut ne pas fournit une valeur de filtre. Vous pouvez fournir une valeur par défaut en ajoutant une valeur par défaut pour l’instance de méthode ou en définissant la valeur par défaut dans le code de votre méthode. Pour plus d’informations sur l’ajout d’une valeur par défaut à l’instance de méthode, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Pour obtenir un exemple montrant comment définir la valeur par défaut d’un paramètre d’entrée dans le code de votre méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validating-the-model"></a>Validation du modèle  
 Vous pouvez valider votre modèle pendant le développement. Visual Studio identifie les problèmes qui peuvent empêcher votre modèle de se comporter comme prévu. Ces problèmes s’affichent dans Visual Studio **liste d’erreurs**.  
  
 Vous pouvez valider un modèle en ouvrant le menu contextuel pour le concepteur BDC, puis en choisissant **Validate**. Si le modèle contient des erreurs, ils apparaissent dans le **liste d’erreurs**. Vous pouvez rapidement déplacer le curseur vers le code qui contient une erreur en double-cliquant sur l’erreur dans la liste. En guise d’alternative, vous pouvez choisir les touches F8 ou MAJ + F8 à plusieurs reprises pour avancer ou reculer dans les erreurs dans la liste.  
  
 Erreurs de validation peuvent se produire lorsque les règles du modèle sont enfreintes d’une certaine façon. Par exemple, si le **IsCollection** d’un descripteur de type est définie sur **true**, mais aucun descripteur de type enfant n’existe, une erreur de validation s’affiche. Vous devrez peut-être faire référence aux règles d’un modèle BDC pour comprendre certaines des erreurs qui s’affichent dans Visual Studio **liste d’erreurs**. Pour plus d’informations sur les règles d’un modèle BDC, consultez [BDCMetadata schéma](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debugging-the-solution-that-contains-the-model"></a>Débogage de la Solution qui contient le modèle  
 Vous pouvez déboguer votre code comme pour n’importe quel code dans Visual Studio. Pour déboguer votre code, définir des points d’arrêt de n’importe où dans votre code et puis démarrez le débogueur. Visual Studio ouvre le site SharePoint. Dans SharePoint, créez une liste ou un composant WebPart qui utilise vos données d’entreprise. Ensuite, vous pouvez parcourir votre code. Pour plus d’informations sur le débogage de projets SharePoint, consultez [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Vous pouvez également déboguer du code dans des assemblys personnalisés que vous ajoutez au projet. Toutefois, pour déboguer le code dans un assembly personnalisé, vous devez ajouter l’assembly au package de solution. Pour plus d’informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Pour plus d’informations sur l’ajout d’un assembly personnalisé à votre projet, consultez [Comment : inclure un Assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configuring-bdc-security"></a>Configuration de la sécurité BDC  
 Vous devrez peut-être modifier vos paramètres de sécurité dans SharePoint avant de pouvoir déboguer votre solution. Pour modifier ces paramètres, ouvrez l’Application de Service de connectivité de données métiers dans le site Web de SharePoint 2010 Central Administration. Dans le **définir des autorisations de magasin de métadonnées** boîte de dialogue, ajoutez votre compte d’utilisateur, puis sélectionnez l’une des options suivantes :  
  
|Tâche|Option|  
|----------|------------|  
|Pour déployer des modèles pour le service BDC.|Modifier|  
|Pour créer des listes et les composants WebPart à l’aide d’externes des types de contenu (entités) dans votre modèle.|Sélectionnable dans les Clients|  
|Pour créer, lire, mettre à jour et supprimer des données d’entité.|Exécuter|  
  
 Pour plus d’informations sur ces paramètres, consultez [gestion des services de connectivité de données métiers](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Vous pouvez également définir des autorisations de sécurité pour les modèles individuels ou des types de contenu externe. Pour plus d’informations sur la façon de définir les autorisations de sécurité d’un modèle, consultez [gérer les modèles BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Pour plus d’informations sur la façon de définir les autorisations de sécurité d’un type de contenu externe, consultez [gestion du type de contenu externe](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Utilisez ces paramètres pour déboguer une solution sur votre serveur SharePoint local. Pour plus d’informations sur la façon de configurer les paramètres de sécurité BDC sur le serveur SharePoint de production, consultez [vue d’ensemble de la sécurité Business Data Connectivity Services](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retracting-models-that-become-corrupt"></a>Retrait des modèles corrompus  
 La première fois que vous démarrez le débogueur, Visual Studio déploie le modèle entier sur SharePoint. Pour chaque fois par la suite, Visual Studio met à jour le modèle dans SharePoint avec les modifications que vous apportez entre les déploiements.  
  
 Il peut y avoir des situations où vous souhaitez que Visual Studio pour retirer le modèle à partir de SharePoint complètement. Par exemple, un modèle peut être endommagé.  Pour redéployer votre modèle sur SharePoint, vous devez définir le **mise à jour incrémentielle** propriété du modèle à **False**, puis démarrez le débogueur. Le **mise à jour incrémentielle** propriété s’affiche dans le **propriétés** lorsque vous sélectionnez le nœud qui représente le modèle dans le **Explorateur BDC**. Par défaut, le nom du modèle est **BdcModel1**.  
  
### <a name="changing-identifier-names-of-entities-in-the-model"></a>Modification des noms d’identificateur d’entités dans le modèle  
 Si vous modifiez le nom d’un identificateur après avoir déployé le modèle, vous pouvez recevoir une erreur de déploiement. Vous ne pouvez pas résoudre cette erreur en définissant le **mise à jour incrémentielle** propriété du modèle à **False**. Vous devez retirer le modèle manuellement et puis redéployez la solution. Pour plus d’informations, consultez [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Vous pouvez éviter cette erreur en définissant le **mise à jour incrémentielle** propriété **False** avant le déploiement initial du modèle.  
  
## <a name="locating-documentation-for-bdc-model-elements"></a>Localisation de Documentation pour les éléments de modèle BDC  
 Visual Studio ajoute un élément XML au modèle pour chaque entité, méthode ou un autre élément que vous créez. Attributs de l’élément s’affichent en tant que propriétés dans le **propriétés** fenêtre. Pour plus d’informations sur les éléments et attributs que Visual Studio génère comme vous concevez le modèle, consultez [BDCMetadata schéma](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)|Décrit les outils que vous pouvez utiliser pour concevoir visuellement un modèle pour le BDC.|  
|[Guide pratique pour ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)|Vous montre comment ajouter des types de contenu externe, ou les entités, au modèle.|  
|[Guide pratique pour ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’afficher une liste d’entités dans une liste ou un composant WebPart.|  
|[Guide pratique pour ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’afficher les détails d’une entité spécifique.|  
|[Guide pratique pour ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs d’ajouter des enregistrements à une source de données directement à partir d’une liste ou un composant WebPart.|  
|[Guide pratique pour ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs de supprimer des données à partir d’une source de données à l’aide des options dans l’Interface utilisateur (UI) d’une liste ou le composant WebPart.|  
|[Guide pratique pour ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)|Vous montre comment ajouter une méthode qui permet aux utilisateurs de modifier des enregistrements de données dans une source de données directement à partir d’une liste ou un composant WebPart.|  
|[Guide pratique pour ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Vous montre comment utiliser la fenêtre Détails de méthode dans Visual Studio pour ajouter des paramètres d’entrée et de retournés à une méthode.|  
|[Guide pratique pour définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Vous montre comment définir des types de données de paramètre dans le modèle.|  
|[Guide pratique pour définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)|Vous montre comment créer une instance d’une méthode que le BDC exécute.|  
|[Guide pratique pour ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Vous montre comment permettre aux utilisateurs limiter le nombre d’instances retourné par une méthode de recherche.|  
|[Création d’une association entre des entités](../sharepoint/creating-an-association-between-entities.md)|Décrit comment vous pouvez définir des relations entre des entités dans le modèle. Les composants WebPart de données de l’entreprise, listes externes et des applications personnalisées peuvent afficher ces relations de données dans une interface utilisateur (IU).|  
|[Comment : créer une Association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md)|Vous montre comment définir des relations entre des entités dans le modèle.|  
|[Procédure pas à pas : création d’une liste externe dans SharePoint à l’aide de données métiers](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fournit des instructions pas à pas qui vous montrent comment créer et tester un modèle qui affiche les contacts dans une liste externe SharePoint.|  
|[Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Fournit une vue d’ensemble de la création et la conception de modèles pour le service BDC.|  
  
  
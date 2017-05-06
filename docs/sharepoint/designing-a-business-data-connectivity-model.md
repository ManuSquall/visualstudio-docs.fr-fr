---
title: "Conception d&#39;un mod&#232;le de connectivit&#233; de donn&#233;es m&#233;tiers"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), concevoir un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), concevoir un modèle"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Conception d&#39;un mod&#232;le de connectivit&#233; de donn&#233;es m&#233;tiers
  Vous pouvez développer un modèle pour le service de connectivité de données métiers \(BDC\) en ajoutant des entités et des méthodes à un fichier modèle.  Une entité décrit une collection de champs de données.  Une entité peut représenter, par exemple, une table dans une base de données.  Une méthode effectue une tâche telle que l'ajout, la suppression ou la mise à jour de données représentées par les entités.  Pour plus d'informations, consultez [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Ajout d'entités  
 Vous pouvez ajouter une entité en faisant glisser ou en copiant une **Entité** de la Boîte à outils **Visual Studio** vers le concepteur BDC.  Pour plus d'informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Définissez les champs de l'entité dans une classe.  Par exemple, vous pouvez ajouter un champ nommé `Address` à une classe `Customer`.  Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à partir d'autres outils, tels que le Concepteur Objet\/Relationnel \(Concepteur O\/R\).  Le nom de l'entité et celui de la classe qui représente l'entité n'ont pas besoin de correspondre.  Vous liez la classe à l'entité lorsque vous définissez les méthodes dans votre modèle.  
  
## Ajout de méthodes  
 Le service BDC appelle des méthodes dans votre modèle lorsque les utilisateurs consultent, ajoutent ou suppriment des informations dans une liste ou un composant WebPart basé sur votre modèle.  Vous devez ajouter une méthode au modèle pour chaque tâche que l'utilisateur peut exécuter.  Créez des méthodes en sélectionnant l'un des cinq types de méthode de base dans la fenêtre **Détails de méthode BDC**.  Le tableau suivant décrit les cinq méthodes de base d'un modèle BDC.  
  
|Méthode|Description|  
|-------------|-----------------|  
|Recherche|Retourne une collection d'instances d'entité.  Appelée lorsque l'utilisateur ouvre la liste ou un composant WebPart.  Pour plus d'informations, consultez [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md).|  
|Recherche spécifique|Retourne une instance d'entité spécifique.  Appelée lorsqu'un utilisateur consulte les détails d'un élément spécifique dans une liste.  Pour plus d'informations, consultez [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Création|Ajoute de nouvelles données à la source de données d'une entité.  Appelée lorsque les utilisateurs choisissent bouton **Nouvel élément** sur le ruban d'une liste basée sur le modèle.  Pour plus d'informations, consultez [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md).|  
|Mise à jour|Modifie les données d'une liste.  Appelée lorsque les utilisateurs mettent à jour les informations dans une liste.  Pour plus d'informations, consultez [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md).|  
|Suppression|Supprime des données.  Appelée lorsque les utilisateurs suppriment un élément dans la liste.  Pour plus d'informations, consultez [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## Définition des paramètres de méthode  
 Lorsque vous créez une méthode, Visual Studio ajoute les paramètres d'entrée et de sortie appropriés au type de méthode.  Ces paramètres sont seulement des espaces réservés.  Dans la plupart des cas, vous devez modifier les paramètres afin qu'ils passent ou retournent le type correct de données.  Par exemple, une méthode de recherche retourne par défaut une chaîne.  Dans la plupart des cas, vous souhaitez modifier le paramètre de retour de la méthode de recherche afin qu'elle retourne une collection d'entités.  Vous pouvez accomplir cela en modifiant le descripteur de type du paramètre.  Un descripteur de type est une collection d'attributs qui décrit le type de données d'un paramètre.  Pour plus d'informations, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio vous permet de copier des descripteurs de type entre des paramètres dans le modèle.  Par exemple, vous pouvez définir un descripteur de type nommé `CustomerTD` pour le paramètre de retour de la méthode `GetCustomer`.  Vous pouvez copier le descripteur de type `CustomerTD` dans l'**Explorateur BDC**, puis coller ce descripteur de type dans le paramètre d'entrée de la méthode `CreateCustomer`.  Cela vous évite de définir le même descripteur de type plusieurs fois.  
  
##  <a name="MethodInstances"></a> Instances de méthode  
 Lorsque vous créez une méthode, Visual Studio ajoute une instance de méthode par défaut.  Une instance de méthode combine une référence à une méthode et les valeurs par défaut des paramètres.  Une méthode unique peut avoir plusieurs instances de méthode.  Chaque instance est une combinaison de la signature de méthode et d'un jeu de valeurs par défaut.  Pour plus d'informations, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Lorsque vous exécutez le projet, les instances de méthode s'affichent dans une liste déroulante au\-dessus de la liste SharePoint.  Les utilisateurs peuvent choisir des instances de méthode pour consulter les données.  
  
 Pour ajouter des valeurs par défaut à l'instance de méthode, vous devez modifier directement le XML du modèle.  Pour plus d'informations, consultez [ValeurParDefaut](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## Ajout de descripteurs de filtre  
 Les consommateurs du modèle peuvent extraire des instances d'une entité qui correspondent à certains critères.  Pour activer cette fonctionnalité, vous pouvez ajouter un descripteur de filtre à une méthode.  Les descripteurs de filtre permettent aux consommateurs de modèle de filtrer des jeux de résultats de méthode en passant des valeurs aux méthodes avant leur exécution.  Pour plus d'informations, consultez [Comment : ajouter des paramètres de filtre aux opérations pour limiter les instances du système externe \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint fournit plusieurs fonctionnalités qui permettent aux utilisateurs de fournir des valeurs de filtre.  Par exemple, les composants WebPart de données métiers fournissent une zone de texte de filtre.  Les utilisateurs peuvent limiter les données contenues dans une liste en entrant une valeur dans la zone de texte.  Pour plus d'informations sur l'ajout d'un descripteur de filtre à une méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### Propriétés du descripteur de filtre  
 Vous devez définir les propriétés **Descripteurs de type associés**, **Nom** et **Type** d'un descripteur de filtre.  Les autres propriétés sont facultatives.  
  
 La propriété **Descripteurs de type associés** lie le descripteur de filtre à un paramètre d'entrée.  Lorsqu'un utilisateur fournit une valeur de filtre, le service BDC passe cette valeur dans la méthode à l'aide du paramètre d'entrée.  
  
 La propriété **Type** décrit le modèle de filtrage que vous souhaitez utiliser.  Dans SharePoint, le modèle de filtrage que vous sélectionnez affecte le texte affiché dans l'interface utilisateur.  Par exemple, pour un modèle de filtrage Comparateur, le texte **est égal à** apparaît comme un contrôle au\-dessus d'un composant WebPart de données métiers.  Pour plus d'informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Pour plus d'informations sur les propriétés d'un descripteur de filtre, consultez [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### Définition de valeurs par défaut  
 Dans certains cas, l'utilisateur peut ne pas fournir une valeur de filtre.  Vous pouvez fournir une valeur par défaut en ajoutant une valeur par défaut à l'instance de méthode ou en définissant la valeur par défaut dans le code de votre méthode.  Pour plus d'informations sur l'ajout d'une valeur par défaut à l'instance de méthode, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  Pour obtenir un exemple de définition de la valeur par défaut d'un paramètre d'entrée dans le code de votre méthode, consultez [Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## Validation du modèle  
 Vous pouvez valider votre modèle pendant le développement.  Visual Studio identifie des problèmes qui peuvent empêcher votre modèle de se comporter comme prévu.  Ces problèmes s'affichent dans la **Liste d'erreurs** Visual Studio.  
  
 Vous pouvez valider un modèle en ouvrant le menu contextuel du concepteur de BDC puis en choisissant **Validation**.  Si le modèle contient des erreurs, elles apparaissent dans **Liste d'erreurs**.  Vous pouvez rapidement déplacer le curseur au code qui contient une erreur en double\-cliquant sur l'erreur dans la liste.  Ou bien, vous pouvez choisir les clés F8 ou Shift\+F8 à plusieurs reprises pour effectuer un pas en avant ou en arrière le long des erreurs dans la liste.  
  
 Des erreurs de validation peuvent se produire lorsque les règles du modèle sont enfreintes d'une façon ou d'une autre.  Par exemple, si la propriété **IsCollection** d'un descripteur de type a la valeur **true**, mais qu'il n'existe aucun descripteur de type enfant, une erreur de validation apparaît.  Vous devrez peut\-être vous reporter aux règles d'un modèle BDC pour comprendre certaines des erreurs qui apparaissent dans la **Liste d'erreurs** Visual Studio.  Pour plus d'informations sur les règles d'un modèle de BDC, consultez [Schéma de BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Débogage de la solution contenant le modèle  
 Vous pouvez déboguer votre code comme vous débogueriez tout code dans Visual Studio.  Pour déboguer votre code, définissez des points d'arrêt n'importe où dans votre code, puis démarrez le débogueur.  Visual Studio ouvre le site SharePoint.  Dans SharePoint, créez une liste ou un composant WebPart qui utilise vos données métiers.  Vous pouvez ensuite exécuter votre code pas à pas.  Pour plus d'informations sur le débogage de projets SharePoint, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Vous pouvez également déboguer le code dans les assemblys personnalisés que vous ajoutez au projet.  Toutefois, pour déboguer le code dans un assembly personnalisé, vous devez ajouter l'assembly au package de solution.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Pour plus d'informations sur l'ajout d'un assembly personnalisé à votre projet, consultez [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### Configuration de la sécurité BDC  
 Vous devrez peut\-être modifier vos paramètres de sécurité dans SharePoint avant de pouvoir déboguer votre solution.  Pour modifier ces paramètres, ouvrez l'application du service de connectivité de données métiers sur le site Web Administration centrale de SharePoint 2010.  Dans la boîte de dialogue **Définir les autorisations du magasin de métadonnées**, ajoutez votre compte d'utilisateur, puis sélectionnez chacune des options suivantes :  
  
|Tâche|Option|  
|-----------|------------|  
|Pour déployer des modèles sur le service BDC.|Modifier|  
|Pour créer des listes et des composants WebPart en utilisant des types de contenu externes \(entités\) dans votre modèle.|Selectable in Clients \(Sélectionnable dans les clients\)|  
|Pour créer, lire, mettre à jour et supprimer des données d'entité.|Execute|  
  
 Pour plus d'informations sur ces paramètres, consultez [Gestion de service de connectivité de données business](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Vous pouvez également définir des autorisations de sécurité pour les modèles individuels ou les types de contenu externes.  Pour plus d'informations sur la manière de définir les autorisations de sécurité d'un modèle, consultez [Gestion des modèles de BDC](http://go.microsoft.com/fwlink/?LinkID=178884).  Pour plus d'informations sur la définition des autorisations de sécurité d'un type de contenu externe, consultez [Gestion des types de contenus externes](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Utilisez ces paramètres pour déboguer une solution sur votre serveur SharePoint local.  Pour plus d'informations sur la configuration de paramètres de sécurité BDC sur le serveur SharePoint de production, consultez [Vue d’ensemble de la sécurité de Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### Retrait des modèles corrompus  
 La première fois que vous démarrez le débogueur, Visual Studio déploie le modèle entier sur SharePoint.  Par la suite, à chaque démarrage, Visual Studio met à jour le modèle dans SharePoint avec toutes les modifications effectuées entre les déploiements.  
  
 Dans certains cas, vous pouvez souhaiter que Visual Studio retire complètement le modèle de SharePoint.  Par exemple, un modèle peut devenir corrompu.  Pour redéployer votre modèle sur SharePoint, affectez à la propriété **Incremental Update** du modèle la valeur **False**, puis démarrez le débogueur.  La propriété **Incremental Update** s'affiche dans la fenêtre **Propriétés** lorsque vous sélectionnez le nœud qui représente le modèle dans l'**Explorateur BDC**.  Par défaut, le nom du modèle est **BdcModel1**.  
  
### Modification des noms d'identificateur des entités du modèle  
 Si vous modifiez le nom d'un identificateur après avoir déployé le modèle, vous risquez de recevoir une erreur de déploiement.  Vous ne pouvez pas résoudre cette erreur en affectant à la propriété **Mise à jour incrémentielle** du modèle la valeur **False**.  Vous devez retirer le modèle manuellement, puis redéployer la solution.  Pour plus d'informations, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  Vous pouvez éviter cette erreur en affectant à la propriété **Mise à jour incrémentielle** la valeur **False** avant le déploiement initial du modèle.  
  
## Recherche de la documentation sur les éléments de modèle BDC  
 Visual Studio ajoute un élément XML au modèle pour chaque entité, méthode ou autre élément que vous créez.  Les attributs d'élément s'affichent en tant que propriétés dans la fenêtre **Propriétés**.  Pour plus d'informations sur les éléments et les attributs que Visual Studio génère comme vous concevez le modèle, consultez [Schéma BDCMetadata \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)|Décrit les outils que vous pouvez utiliser afin de concevoir visuellement un modèle pour le BDC.|  
|[Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)|Indique comment ajouter des types de contenu externes, ou entités, au modèle.|  
|[Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)|Indique comment ajouter une méthode qui permet aux utilisateurs de consulter une liste d'entités dans une liste ou un composant WebPart.|  
|[Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)|Indique comment ajouter une méthode qui permet aux utilisateurs de consulter les détails d'une entité spécifique.|  
|[Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)|Indique comment ajouter une méthode qui permet aux utilisateurs d'ajouter directement des enregistrements à une source de données à partir d'une liste ou d'un composant WebPart.|  
|[Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)|Indique comment ajouter une méthode qui permet aux utilisateurs de supprimer des données d'une source de données à l'aide des options dans l'interface utilisateur d'une liste ou d'un composant WebPart.|  
|[Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)|Indique comment ajouter une méthode qui permet aux utilisateurs de modifier directement des enregistrements de données dans une source de données à partir d'une liste ou d'un composant WebPart.|  
|[Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Indique comment utiliser la fenêtre Détails de méthode dans Visual Studio pour ajouter des paramètres d'entrée et de retour à une méthode.|  
|[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Indique comment définir des types de données de paramètre dans le modèle.|  
|[Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)|Indique comment créer une instance d'une méthode que le BDC exécute.|  
|[Comment : ajouter un descripteur de filtre à une méthode de recherche](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Indique comment permettre aux utilisateurs de limiter le nombre d'instances retourné par une méthode de recherche.|  
|[Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md)|Décrit comment vous pouvez définir des relations entre des entités dans le modèle.  Les composants WebPart de données métiers, les listes externes et les applications personnalisées peuvent afficher ces relations de données dans une interface utilisateur.|  
|[Comment : créer une association entre des entités](../sharepoint/how-to-create-an-association-between-entities.md)|Indique comment définir des relations entre des entités dans le modèle.|  
|[Procédure pas à pas : création d'une liste externe dans SharePoint à l'aide de données métiers](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fournit des instructions pas à pas qui indiquent comment créer et tester un modèle affichant des contacts dans une liste externe SharePoint.|  
|[Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Fournit une vue d'ensemble de la création et de la conception de modèles pour le service BDC.|  
  
  
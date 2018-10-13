---
title: Création d’Applications de données | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291308"
---
# <a name="creating-data-applications"></a>Création d'applications de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio fournit de nombreux outils au moment du design pour vous aider à créer des applications qui accèdent aux données. Cette introduction présente une vue d'ensemble des processus de base impliqués dans la création d'applications qui utilisent des données. Les informations de cette section ignorent délibérément de nombreux détails et constituent une source d'informations et un point de départ vers les nombreuses pages d'aide relatives à la création d'une application de données.  
  
 Au fur et à mesure que vous développerez des applications d’accès aux données dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vos exigences seront différentes. Dans certains cas, vous voudrez simplement afficher des données dans un formulaire. Dans d'autres, vous devrez imaginer un moyen de partager des informations avec d'autres applications ou processus.  
  
 Quelles que soient les opérations que vous exécutez avec les données, il est important de comprendre certains concepts fondamentaux. Vous n'aurez probablement jamais besoin de connaître certains détails de la gestion des données — vous n'aurez, par exemple, probablement jamais besoin de créer une base de données par programmation — mais il est très utile de comprendre les concepts de données de base, ainsi que les outils de données (Assistants et concepteurs) disponibles dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Une application de données standard utilise la plupart des processus illustrés dans le diagramme suivant :  
  
 ![Graphique Cycle de données](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
Cycle des données  
  
 Au fur et à mesure que vous créez votre application, pensez à la tâche que vous essayez d’accomplir. Utilisez les sections suivantes pour vous aider à rechercher les outils [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et les objets qui sont mis à votre disposition.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des Assistants pour simplifier plusieurs processus affichés dans le diagramme précédent. Par exemple, en cours d’exécution le **Assistant de Configuration de Source de données** fournit à votre application suffisamment d’informations pour se connecter aux données, créer un dataset typé pour recevoir les données et importer les données dans votre application.  
  
 Pour voir rapidement comment [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous aide à développer des applications de données, consultez [procédure pas à pas : création d’une Application de données Simple](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Connexion aux données  
 Pour importer des données dans votre application (et renvoyer les modifications à la source de données), une certaine communication bidirectionnelle doit être établie. Cette communication bidirectionnelle est généralement contrôlée par les objets dans votre modèle de données.  
  
 Par exemple, `TableAdapter` connecte les applications qui utilisent des groupes de données à une base de données et <xref:System.Data.Objects.ObjectContext> connecte des entités du Entity Framework à une base de données. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit plusieurs outils pour vous aider à créer des connexions qui peuvent être utilisées par votre application. Pour plus d’informations sur la connexion de votre application aux données, consultez [connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Pour savoir comment utiliser des jeux de données pour connecter votre application aux données dans une base de données, consultez [procédure pas à pas : connexion aux données dans une base de données (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Préparation de votre application pour recevoir des données  
 Si votre application utilise un modèle de données déconnecté, vous devez stocker temporairement les données dans votre application pendant que vous utilisez ce modèle. Visual Studio propose des outils pour vous aider à créer les objets que votre application utilise pour stocker des données temporairement : groupes de données, entités et objets [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Une application qui utilise un modèle de données déconnecté se connecte généralement à une base de données, exécute une requête qui importe des données dans l'application, se déconnecte de la base de données, puis manipule les données hors connexion avant de se reconnecter et de mettre à jour la base de données.  
  
 Pour plus d’informations sur la création de datasets typés dans votre application, consultez [préparation de votre Application pour recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Pour plus d’informations sur l’utilisation de jeux de données dans les applications multicouches, consultez [séparer les datasets et les TableAdapters dans différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Pour savoir comment créer un jeu de données, exécutez les procédures décrites dans [procédure pas à pas : création d’un Dataset avec le Concepteur de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Pour apprendre à créer [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objets, effectuez les procédures dans [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Récupération de données dans votre application  
 Que votre application utilise ou non un modèle de données déconnecté, vous devez être capable d'extraire des données dans votre application. Pour importer des données dans votre application, vous devez exécuter des requêtes ou des procédures stockées sur une base de données. Applications qui stockent des données dans les jeux de données exécutent des requêtes et des procédures stockées à l’aide de `TableAdapter`s, tandis que les applications qui stockent les données dans les entités exécutent des requêtes à l’aide de [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) ou en vous connectant des entités directement à des procédures stockées. Pour plus d’informations sur la création et modification des requêtes qui utilisent des TableAdapters, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) et [Comment : modifier les requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Pour plus d’informations sur le chargement des données en jeux de données, ainsi que sur l’exécution de requêtes et des procédures stockées, consultez [l’extraction des données dans votre Application](../data-tools/fetching-data-into-your-application.md).  
  
 Pour savoir comment charger des données dans un jeu de données, exécutez les procédures décrites dans [procédure pas à pas : affichage des données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) et examinez le code dans le Gestionnaire d’événements de chargement de formulaire.  
  
 Pour savoir comment charger des données dans [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objets, effectuez les procédures dans [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Pour savoir comment créer et exécuter une requête SQL, consultez [Comment : créer et exécuter une instruction SQL qui retourne les lignes](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Pour savoir comment exécuter une procédure stockée, consultez [Comment : exécuter une procédure stockée qui retourne les lignes](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Affichage des données dans les formulaires  
 Après avoir ajouté des données dans votre application, vous les affichez généralement dans un formulaire afin que les utilisateurs puissent les voir ou les modifier. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit le [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), où vous pouvez faire glisser des éléments sur des formulaires pour créer automatiquement des contrôles liés aux données qui affichent des données. Pour plus d’informations sur la liaison de données et affichage des données pour les utilisateurs, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Pour savoir comment présenter des données aux utilisateurs, exécutez les procédures décrites dans les procédures suivantes (en faisant particulièrement attention au processus consistant à faire glisser des éléments à partir de la **des Sources de données** fenêtre) :  
  
-   [Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Procédure pas à pas : Liaison de contrôles Silverlight à un Service de données WCF](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Modification des données dans votre application  
 Une fois les données présentées à vos utilisateurs, ils souhaiteront probablement les modifier en ajoutant de nouveaux enregistrements ainsi qu'en modifiant et en supprimant des enregistrements avant de renvoyer les données à la base de données.  
  
 Pour plus d’informations sur l’utilisation des données une fois qu’il est chargé dans votre jeu de données, consultez [modification des données dans votre Application](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Validation des données  
 Lorsque vous modifiez des données, vous souhaitez généralement vérifier les modifications avant d'autoriser l'acceptation des valeurs dans le groupe de données ou leur écriture dans la base de données. *Validation* est le nom du processus pour vérifier que ces nouvelles valeurs sont acceptables pour les besoins de votre application. Vous pouvez ajouter une logique pour vérifier les valeurs dans votre application au fur et à mesure de leur modification. Visual Studio propose des outils pour vous aider à ajouter du code qui valide les données pendant la modification des colonnes et des lignes. Pour plus d’informations, consultez [validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Pour savoir comment ajouter la validation de données à votre application, consultez [procédure pas à pas : ajout d’une Validation à un Dataset](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Pour savoir comment ajouter la validation à un jeu de données séparé dans une application multicouche, consultez [ajouter la validation à un jeu de données multicouches](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Enregistrement de données  
 Lorsque vous avez apporté des modifications à votre application (et que vous les avez validées), vous souhaitez généralement les renvoyer à la base de données. Les applications qui stockent des données dans les groupes de données utilisent en général un TableAdapterManager pour enregistrer les données. Pour plus d’informations, consultez [vue d’ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Applications Entity Framework utilisent la <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> méthode pour enregistrer les données.  
  
 Pour plus d’informations sur l’envoi de données mises à jour vers une base de données, consultez [l’enregistrement des données](../data-tools/saving-data.md).  
  
 Pour savoir comment envoyer des données mises à jour à partir d’un jeu de données à une base de données, exécutez les procédures décrites dans [procédure pas à pas : enregistrement de données à partir des Tables de données connexes (mise à jour hiérarchique)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Rubriques connexes  
 [Vue d’ensemble des applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Fournit des liens vers les rubriques qui expliquent comment créer des applications qui utilisent les données.  
  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Fournit des liens vers des rubriques expliquant comment utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour connecter votre application aux données et créer des sources de données pour vos applications.  
  
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Fournit des liens vers les rubriques qui expliquent comment utiliser des modèles de données dans votre application, notamment les groupes de données et les Entity Data Models.  
  
 [Récupération de données dans votre application](../data-tools/fetching-data-into-your-application.md)  
 Fournit des liens vers les rubriques qui expliquent comment charger des données dans votre application.  
  
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Fournit des liens vers les rubriques qui expliquent comment lier des contrôles Windows Forms, WPF et Silverlight aux sources de données.  
  
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)  
 Fournit des liens vers les rubriques qui décrivent comment modifier des données dans votre application.  
  
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Fournit des liens vers les rubriques qui décrivent comment ajouter la validation aux modifications de données.  
  
 [Enregistrer des données](../data-tools/saving-data.md)  
 Fournit des liens vers les rubriques qui expliquent comment envoyer des données mises à jour de votre application vers une base de données, ou comment les enregistrer dans d'autres formats tel que le format XML.  
  
 [Outils permettant de travailler avec des Sources de données dans Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Fournit des liens vers des rubriques traitant des outils que vous pouvez utiliser pour travailler avec des sources de données dans Visual Studio, telles que la **des Sources de données** fenêtre et ADO.NET Entity Data Model Designer.
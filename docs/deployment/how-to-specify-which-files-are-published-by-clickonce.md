---
title: 'Comment : spécifier les fichiers publiés via ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c59ffc2324f25c42b505505b0dbea9160ef023a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561413"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Comment : spécifier les fichiers publiés via ClickOnce
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, de non code des fichiers dans le projet sont déployés avec l’application. Dans certains cas, vous ne pouvez pas voulez ou devez publier certains fichiers, ou vous souhaiterez installer certains fichiers selon des conditions. Visual Studio fournit les fonctionnalités pour exclure des fichiers, marquer des fichiers comme fichiers de données ou des conditions préalables requises et créer des groupes de fichiers pour une installation conditionnelle.  
  
 Fichiers pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application sont gérées dans le **fichiers d’Application** boîte de dialogue, accessible à partir de la **publier** page de la **Concepteur de projets**.  
  
 Initialement, il existe un seul groupe de fichiers nommé **(obligatoire)**. Vous pouvez créer des groupes de fichiers supplémentaires et leur attribuer des fichiers. Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour exécuter l’application. Par exemple, .exe de l’application ou les fichiers marqués comme fichiers de données doivent appartenir à la **(obligatoire)** groupe.  
  
 État de publication de la valeur par défaut la valeur d’un fichier est marquée avec **(Auto)**. Par exemple, .exe l’application a un état de publication de **Include (Auto)** par défaut.  
  
 Les fichiers avec le **Action de génération** propriété **contenu** sont désignés comme fichiers d’application et seront marqués comme inclus par défaut. Elles pouvant être inclus, exclus ou marqués en tant que fichiers de données. Les exceptions sont les suivantes :  
  
-   Fichiers de données tels que les fichiers de base de données SQL (.mdf et .mdb) et les fichiers XML portera la mention des fichiers de données par défaut.  
  
-   Références aux assemblys (fichiers .dll) sont désignées comme suit lorsque vous ajoutez la référence : si **copie locale** est **False**, il est marqué par défaut comme assembly requis (**(configuration requise Auto)**) qui doit être présent dans le GAC, avant que l’application est installée. Si **copie locale** est **True**, l’assembly est marqué par défaut comme un assembly d’application (**Include (Auto)**) et sera copié dans le dossier d’application lors de l’installation. Une référence COM s’affiche dans le **fichiers d’Application** boîte de dialogue case (comme un fichier .ocx) uniquement si son **isolé** est définie sur **True**. Par défaut, il sera inclus.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Pour ajouter des fichiers à la boîte de dialogue fichiers Application  
  
1.  Sélectionnez un fichier de données dans **l’Explorateur de solutions**.  
  
2.  Dans la fenêtre Propriétés, modifiez la **Action de génération** propriété le **contenu** valeur.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Pour exclure des fichiers à partir de la publication ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le fichier que vous souhaitez exclure.  
  
5.  Dans le **état de la publication** champ, sélectionnez **exclure** dans la liste déroulante.  
  
### <a name="to-mark-files-as-data-files"></a>Pour marquer les fichiers en tant que fichiers de données  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le fichier que vous souhaitez marquer en tant que données.  
  
5.  Dans le **état de la publication** champ, sélectionnez **fichier de données** dans la liste déroulante.  
  
### <a name="to-mark-files-as-prerequisites"></a>Pour marquer les fichiers comme composants requis  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez l’assembly d’application (fichier .dll) que vous souhaitez marquer comme composant requis. Notez que votre application doit avoir une référence à l’assembly d’application afin qu’il apparaisse dans la liste.  
  
5.  Dans le **état de la publication** champ, sélectionnez **requis** dans la liste déroulante.  
  
### <a name="to-add-a-new-file-group"></a>Pour ajouter un nouveau groupe de fichiers  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le **groupe** field pour un fichier que vous souhaitez inclure dans le nouveau groupe.  
  
    > [!NOTE]
    >  Les fichiers doivent avoir le **Action de génération** propriété **contenu** avant que les noms de fichiers apparaissent dans le **fichiers d’Application** boîte de dialogue.  
  
5.  Dans le **groupe de téléchargement** champ, sélectionnez  **\<nouveau... >** dans la liste déroulante.  
  
6.  Dans le **nouveau groupe** boîte de dialogue, entrez un nom pour le groupe, puis cliquez sur **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Pour ajouter un fichier à un groupe  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le **groupe** field pour un fichier que vous souhaitez inclure dans le nouveau groupe.  
  
5.  Dans le **groupe de téléchargement** , sélectionnez un groupe dans la liste déroulante.  
  
    > [!NOTE]
    >  Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour exécuter l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
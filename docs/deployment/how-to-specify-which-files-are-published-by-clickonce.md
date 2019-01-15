---
title: 'Procédure : Spécifier les fichiers publiés par ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: e11c336f891ae71968a3b325a66a50d4d9a79446
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826953"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Procédure : Spécifier les fichiers publiés par ClickOnce
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fichiers d’application, sans code dans le projet sont déployés avec l’application. Dans certains cas, vous ne pouvez pas souhaitez ou devez publier certains fichiers, ou vous souhaiterez installer certains fichiers selon des conditions. Visual Studio fournit les fonctionnalités pour exclure des fichiers, marquer des fichiers comme fichiers de données ou des conditions préalables et créer des groupes de fichiers pour une installation conditionnelle.  
  
 Fichiers pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application sont gérées dans le **fichiers d’Application** boîte de dialogue, accessible à partir de la **publier** page de la **Concepteur de projet**.  
  
 Initialement, il existe un seul groupe de fichiers nommé **(obligatoire)**. Vous pouvez créer des groupes de fichiers supplémentaires et leur attribuer des fichiers. Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour exécuter l’application. Par exemple, .exe de l’application ou les fichiers marqués comme fichiers de données doivent appartenir à la **(obligatoire)** groupe.  
  
 État de publication de la valeur par défaut la valeur d’un fichier est marquée avec **(Auto)**. Par exemple, .exe l’application a un état de publication de **inclure (automatique)** par défaut.  
  
 Fichiers avec le **Action de génération** propriété définie sur **contenu** sont désignés en tant que fichiers d’application et seront marqués comme inclus par défaut. Elles pouvant être inclus, exclus ou marqués comme fichiers de données. Les exceptions sont les suivantes :  
  
-   Fichiers de données comme base de données SQL (*.mdf* et *.mdb*) fichiers et les fichiers XML sont marqués en tant que fichiers de données par défaut.  
  
-   Références aux assemblys (*.dll* fichiers) sont désignées comme suit quand vous ajoutez la référence : Si **copie locale** est **False**, il est marqué par défaut comme assembly requis (**condition préalable (Auto)**) qui doit être présent dans le GAC avant que l’application est installée. Si **copie locale** est **True**, l’assembly est marqué par défaut comme un assembly d’application (**inclure (automatique)**) et sera copié dans le dossier d’application lors de l’installation. Une référence COM s’affichera dans le **fichiers d’Application** boîte de dialogue (comme un *.ocx* fichier) uniquement si son **isolé** propriété est définie sur **True**. Par défaut, il sera inclus.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Pour ajouter des fichiers à la boîte de dialogue fichiers d’Application  
  
1.  Sélectionnez un fichier de données dans **l’Explorateur de solutions**.  
  
2.  Dans la fenêtre Propriétés, modifiez le **Action de génération** propriété le **contenu** valeur.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Pour exclure des fichiers à partir de la publication ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le fichier que vous souhaitez exclure.  
  
5.  Dans le **état de la publication** champ, sélectionnez **exclure** dans la liste déroulante.  
  
### <a name="to-mark-files-as-data-files"></a>Pour marquer les fichiers en tant que fichiers de données  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le fichier que vous souhaitez marquer en tant que données.  
  
5.  Dans le **état de la publication** champ, sélectionnez **fichier de données** dans la liste déroulante.  
  
### <a name="to-mark-files-as-prerequisites"></a>Pour marquer les fichiers comme composants requis  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez l’assembly d’application (*.dll* fichier) que vous souhaitez marquer comme condition préalable. Notez que votre application doit avoir une référence à l’assembly d’application afin qu’il apparaisse dans la liste.  
  
5.  Dans le **état de la publication** champ, sélectionnez **prérequis** dans la liste déroulante.  
  
### <a name="to-add-a-new-file-group"></a>Pour ajouter un nouveau groupe de fichiers  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le **groupe** field pour un fichier que vous souhaitez inclure dans le nouveau groupe.  
  
    > [!NOTE]
    >  Les fichiers doivent avoir le **Action de génération** propriété définie sur **contenu** avant que les noms de fichiers n’apparaissent dans le **fichiers d’Application** boîte de dialogue.  
  
5.  Dans le **groupe de téléchargement** champ, sélectionnez  **\<nouveau... >** dans la liste déroulante.  
  
6.  Dans le **nouveau groupe** boîte de dialogue, entrez un nom pour le groupe, puis cliquez sur **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Pour ajouter un fichier à un groupe  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Cliquez sur le **fichiers d’Application** bouton pour ouvrir la **fichiers d’Application** boîte de dialogue.  
  
4.  Dans le **fichiers d’Application** boîte de dialogue, sélectionnez le **groupe** field pour un fichier que vous souhaitez inclure dans le nouveau groupe.  
  
5.  Dans le **groupe de téléchargement** , sélectionnez un groupe dans la liste déroulante.  
  
    > [!NOTE]
    >  Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour exécuter l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
---
title: Spécifier les fichiers à publier (ClickOnce)
description: Découvrez comment exclure des fichiers, marquer des fichiers comme des fichiers de données ou des composants requis, et créer des groupes pour une installation conditionnelle pour une application ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d093438dc30bee08abbc45c6cf3c2555fbe208c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887482"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Guide pratique pour spécifier les fichiers publiés par ClickOnce
Lors de la publication d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, tous les fichiers qui ne sont pas du code dans le projet sont déployés en même temps que l’application. Dans certains cas, il se peut que vous ne souhaitiez pas ou ayez besoin de publier certains fichiers, ou que vous souhaitiez installer certains fichiers en fonction de conditions. Visual Studio fournit les fonctionnalités permettant d’exclure des fichiers, de marquer des fichiers comme fichiers de données ou composants requis, et de créer des groupes de fichiers pour une installation conditionnelle.

 Les fichiers d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application sont gérés dans la boîte de dialogue **fichiers d’application** , accessible à partir de la page **publier** du **Concepteur de projet**.

 Au départ, il existe un seul groupe de fichiers nommé **(obligatoire)**. Vous pouvez créer des groupes de fichiers supplémentaires et leur assigner des fichiers. Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour l’exécution de l’application. Par exemple, le fichier. exe de l’application ou les fichiers marqués comme fichiers de données doivent appartenir au groupe **(obligatoire)** .

 La valeur par défaut de l’état de publication d’un fichier est marquée avec **(auto)**. Par exemple, le fichier. exe de l’application a l’état de publication **include (auto)** par défaut.

 Les fichiers dont la propriété **action de génération** a la valeur **contenu** sont désignés en tant que fichiers d’application et sont marqués comme inclus par défaut. Ils peuvent être inclus, exclus ou marqués comme fichiers de données. Les exceptions sont les suivantes :

- Les fichiers de données tels que les fichiers SQL Database (*. mdf* et *. mdb*) et les fichiers XML sont marqués comme fichiers de données par défaut.

- Les références aux assemblys (fichiers *. dll* ) sont désignées comme suit quand vous ajoutez la référence : si **copie locale** a la **valeur false**, elle est marquée par défaut comme un assembly requis (**condition préalable (auto)**) qui doit être présent dans le GAC avant l’installation de l’application. Si **copie locale** a la **valeur true**, l’assembly est marqué par défaut en tant qu’assembly d’application (**include (auto)**) et sera copié dans le dossier de l’application au moment de l’installation. Une référence COM apparaîtra dans la boîte de dialogue **fichiers d’application** (sous la forme d’un fichier *. ocx* ) uniquement si sa propriété **isolé** a la valeur **true**. Par défaut, il est inclus.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Pour ajouter des fichiers à la boîte de dialogue fichiers d’application

1. Sélectionnez un fichier de données dans **Explorateur de solutions**.

2. Dans le Fenêtre Propriétés, remplacez la valeur de la propriété **action de génération** par la valeur **contenu** .

### <a name="to-exclude-files-from-clickonce-publishing"></a>Pour exclure des fichiers de la publication ClickOnce

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **fichiers d’application** pour ouvrir la boîte de dialogue **fichiers d’application** .

4. Dans la boîte de dialogue **fichiers d’application** , sélectionnez le fichier que vous souhaitez exclure.

5. Dans le champ État de la **publication** , sélectionnez **exclure** dans la liste déroulante.

### <a name="to-mark-files-as-data-files"></a>Pour marquer des fichiers en tant que fichiers de données

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **fichiers d’application** pour ouvrir la boîte de dialogue **fichiers d’application** .

4. Dans la boîte de dialogue **fichiers d’application** , sélectionnez le fichier que vous souhaitez marquer comme données.

5. Dans le champ État de la **publication** , sélectionnez **fichier de données** dans la liste déroulante.

### <a name="to-mark-files-as-prerequisites"></a>Pour marquer les fichiers comme composants requis

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **fichiers d’application** pour ouvrir la boîte de dialogue **fichiers d’application** .

4. Dans la boîte de dialogue **fichiers d’application** , sélectionnez l’assembly d’application (fichier *. dll* ) que vous souhaitez marquer comme composant requis. Notez que votre application doit avoir une référence à l’assembly d’application afin qu’elle s’affiche dans la liste.

5. Dans le champ État de la **publication** , sélectionnez **composant requis** dans la liste déroulante.

### <a name="to-add-a-new-file-group"></a>Pour ajouter un nouveau groupe de fichiers

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **fichiers d’application** pour ouvrir la boîte de dialogue **fichiers d’application** .

4. Dans la boîte de dialogue **fichiers d’application** , sélectionnez le champ **groupe** pour un fichier que vous souhaitez inclure dans le nouveau groupe.

    > [!NOTE]
    > La propriété action de **génération** des fichiers doit être définie sur **contenu** avant que les noms de fichiers ne s’affichent dans la boîte de dialogue **fichiers d’application** .

5. Dans le champ **groupe de téléchargement** , sélectionnez **\<New...>** dans la liste déroulante.

6. Dans la boîte de dialogue **nouveau groupe** , entrez un nom pour le groupe, puis cliquez sur **OK**.

### <a name="to-add-a-file-to-a-group"></a>Pour ajouter un fichier à un groupe

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Cliquez sur le bouton **fichiers d’application** pour ouvrir la boîte de dialogue **fichiers d’application** .

4. Dans la boîte de dialogue **fichiers d’application** , sélectionnez le champ **groupe** pour un fichier que vous souhaitez inclure dans le nouveau groupe.

5. Dans le champ **groupe de téléchargement** , sélectionnez un groupe dans la liste déroulante.

    > [!NOTE]
    > Vous ne pouvez pas modifier le **groupe de téléchargement** pour les fichiers qui sont requis pour l’exécution de l’application.

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
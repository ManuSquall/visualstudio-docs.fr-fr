---
title: Guide pratique pour signer des manifestes d’application et de déploiement
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf25301095ac5ff438514c37f61337e46342860
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596162"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Guide pratique pour signer des manifestes d’application et de déploiement

Si vous souhaitez publier une application à l’aide du déploiement ClickOnce, vous devez signer les manifestes d’application et de déploiement avec une paire de clés publique/privée et à l’aide de la technologie Authenticode. Vous pouvez signer les manifestes à l’aide d’un certificat à partir du magasin de certificats Windows ou d’un fichier de clé.

Pour plus d’informations sur le déploiement ClickOnce, consultez [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md).

La signature des manifestes ClickOnce est facultative pour les applications *.exe*. Pour plus d’informations, consultez la section « Générer des manifestes non signés » de ce document.

Pour plus d’informations sur la création de fichiers de clés, consultez [Guide pratique pour créer une paire de clés publique/privée](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Visual Studio prend uniquement en charge les fichiers de clés PFX (Personal Information Exchange) ayant l’extension *.pfx*. Toutefois, vous pouvez sélectionner d’autres types de certificats à partir du magasin de certificats Windows de l’utilisateur actuel en cliquant sur **Sélectionner dans Store** dans la page **Signature** des propriétés du projet.

## <a name="sign-using-a-certificate"></a>Signer en utilisant un certificat

1. Accédez à la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’**Explorateur de solutions** et sélectionnez **Propriétés**). Sous l’onglet **Signature**, cochez la case **Signer les manifestes ClickOnce**.

2. Cliquez sur le bouton **Sélectionner dans Store**.

     La boîte de dialogue **Sélectionner un certificat** apparaît et affiche le contenu du magasin de certificats Windows.

    > [!TIP]
    > Si vous cliquez sur **Cliquez ici pour afficher les propriétés du certificat**, la boîte de dialogue **Détails du certificat** s’affiche. Cette boîte de dialogue contient des informations détaillées sur le certificat et des options supplémentaires. Cliquez sur **Certificats** pour voir des informations d’aide supplémentaires.

3. Sélectionnez le certificat que vous souhaitez utiliser pour signer les manifestes.

4. Vous pouvez aussi spécifier l’adresse d’un serveur d’horodatage dans la zone de texte **URL du serveur d’horodatage**. Ce serveur fournit un horodatage spécifiant quand le manifeste a été signé.

## <a name="sign-using-an-existing-key-file"></a>Signer en utilisant un fichier de clé existant

1. Dans la page **Signature**, cochez la case **Signer les manifestes ClickOnce**.

2. Cliquez sur le bouton **À partir d’un fichier**.

     La boîte de dialogue **Sélectionner le fichier** s’affiche.

3. Dans la boîte de dialogue **Sélectionner le fichier**, accédez à l’emplacement du fichier de clé ( *.pfx*) à utiliser, puis cliquez sur **Ouvrir**.

    > [!NOTE]
    > Cette option prend uniquement en charge les fichiers ayant l’extension *.pfx*. Si vous avez un fichier de clé ou un certificat dans un autre format, stockez-le dans le magasin de certificats Windows et sélectionnez le certificat, comme indiqué dans la procédure précédente. L’objet du certificat sélectionné doit inclure la signature de code.

     La boîte de dialogue **Entrez le mot de passe pour ouvrir le fichier** s’affiche. (Si le fichier *.pfx* est déjà stocké dans votre magasin de certificats Windows ou s’il n’est pas protégé par un mot de passe, vous n’êtes pas invité à entrer un mot de passe.)

4. Entrez le mot de passe pour accéder au fichier de clé, puis sélectionnez **Entrée**.

> [!NOTE]
> Le fichier *.pfx* ne peut pas inclure d’informations de chaînage des certificats. Si c’est le cas, l’erreur d’importation suivante se produit : **le certificat et la clé privée sont introuvables pour le déchiffrement**. Pour supprimer les informations de chaînage de certificats, vous pouvez utiliser *Certmgr. msc* et [désactiver l’option](/previous-versions/aa730868(v=vs.80)) permettant d' **inclure tous les certificats** lors de l’exportation du fichier *. pfx.

## <a name="sign-using-a-test-certificate"></a>Signer en utilisant un certificat de test

1. Dans la page **Signature**, cochez la case **Signer les manifestes ClickOnce**.

2. Pour créer un certificat de test, cliquez sur le bouton **Créer un certificat de test**.

3. Dans la boîte de dialogue **Créer un certificat de test**, entrez un mot de passe pour sécuriser votre certificat de test.

## <a name="generate-unsigned-manifests"></a>Générer des manifestes non signés

La signature des manifestes ClickOnce est facultative pour les applications *.exe*. Les procédures suivantes montrent comment générer des manifestes ClickOnce non signés.

> [!IMPORTANT]
> Les manifestes non signés peuvent simplifier le développement et le test de votre application. Toutefois, ils présentent des problèmes de sécurité importants dans un environnement de production. N’envisagez l’utilisation de manifestes non signés que si votre application ClickOnce s’exécute sur des ordinateurs au sein d’un intranet complètement isolé d’Internet ou d’autres sources de code malveillant.

Par défaut, ClickOnce génère automatiquement des manifestes signés, sauf si un ou plusieurs fichiers sont spécifiquement exclus du hachage généré. En d’autres termes, la publication de l’application aboutit à des manifestes signés si tous les fichiers sont inclus dans le hachage, même si la case **Signer les manifestes ClickOnce** n’est pas cochée.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Pour générer des manifestes non signés et inclure tous les fichiers dans le hachage généré

1. Pour générer des manifestes non signés qui incluent tous les fichiers dans le hachage, vous devez d’abord publier l’application avec des manifestes signés. Vous devez donc signer les manifestes ClickOnce en effectuant l’une des procédures précédentes, puis publier l’application.

2. Dans la page **Signature**, décochez la case **Signer les manifestes ClickOnce**.

3. Redéfinissez la version de publication afin qu’une seule version de votre application soit disponible. Par défaut, Visual Studio incrémente automatiquement le numéro de révision de la version de publication chaque fois que vous publiez une application. Pour plus d’informations, consultez [Guide pratique pour définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Publiez l'application.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Pour générer des manifestes non signés et exclure un ou plusieurs fichiers du hachage généré

1. Dans la page **Signature**, décochez la case **Signer les manifestes ClickOnce**.

2. Ouvrez la boîte de dialogue **Fichiers d’application** et définissez le **Hachage** sur **Exclure** pour les fichiers que vous souhaitez exclure du hachage généré.

    > [!NOTE]
    > Quand un fichier est exclu du hachage, ClickOnce est configuré pour désactiver la signature automatique des manifestes ; vous n’avez donc pas besoin de procéder à une publication préalable avec des manifestes signés comme indiqué dans la procédure précédente.

3. Publiez l'application.

## <a name="see-also"></a>Voir aussi

- [Assemblys avec nom fort](/dotnet/framework/app-domains/strong-named-assemblies)
- [Guide pratique pour créer une paire de clés publique/privée](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Signature, page du Concepteur de projets](../ide/reference/signing-page-project-designer.md)
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)

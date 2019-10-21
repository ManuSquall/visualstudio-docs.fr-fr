---
title: 'Comment : sélectionner les schémas XML à utiliser | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666507"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : sélectionner les schémas XML à utiliser
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'Éditeur XML fournit un cache de schéma dans le répertoire %InstallDir%\Xml\Schemas. Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.

 La propriété de document **schemas** permet de sélectionner un ou plusieurs schémas en langage XSD (XML Schema Definition) à utiliser. Elle permet de choisir des schémas dans le cache de schéma ou de spécifier un schéma situé ailleurs dans le cache.

 Les schémas spécifiés sont enregistrés dans le fichier masqué d'options utilisateur de la solution (.suo), avec toutes les autres propriétés de document XML. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

> [!NOTE]
> L'éditeur peut effectuer la validation à l'aide d'un schéma inline ou d'un schéma dont la référence est fournie par l'attribut `xsd:schemaLocation`. Pour plus d’informations, consultez [validation de document XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML dans le cache de schéma

1. Ouvrez un fichier dans l'éditeur XML.

2. Dans la fenêtre Propriétés du document, cliquez sur le bouton dans le champ **schémas** .

    La boîte de dialogue **schémas XML** s’affiche. La boîte de dialogue répertorie tous les schémas dotés d’une extension. xsd dans le cache de schéma (y compris les schémas référencés dans le fichier catalog. Xml), ainsi que tous les schémas de la solution actuelle, ouverts dans Visual Studio, référencés dans un attribut `xsd:schemaLocation`, ou référencés dans le Propriété **schemas** .

3. Sélectionnez les schémas à utiliser pour la validation en effectuant l'une des opérations suivantes :

   - Sélectionnez un schéma listé dans la boîte de dialogue **schémas XML** , cliquez sur la colonne **utiliser** , puis sélectionnez **utiliser ce schéma**.

     ou

   - Sélectionnez plusieurs schémas listés dans la boîte de dialogue **schémas XML** , cliquez avec le bouton droit et sélectionnez **utiliser ce schéma**.

4. Cliquez sur **OK**.

    La liste des schémas sélectionnés est recopiée dans la propriété de document **schemas** .

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Pour ajouter un schéma XML au cache de schéma

1. Dans la fenêtre Propriétés du document, cliquez sur le bouton dans le champ **schémas** .

2. Cliquez sur **Ajouter**.

     La boîte de dialogue **ouvrir le schéma XSD** s’ouvre.

3. Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.

4. Cliquez sur **Ouvrir**.

     Le ou les schémas ont été ajoutés au cache de schéma et la valeur de la colonne **use** est définie pour **utiliser ce schéma**.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Pour supprimer un schéma XML du cache de schéma

1. Dans la fenêtre Propriétés du document, cliquez sur le bouton dans le champ **schémas** .

2. Sélectionnez le schéma à supprimer, puis cliquez sur **supprimer**.

     Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.

    > [!NOTE]
    > Si vous avez toujours une référence au schéma via un attribut `schemaLocation`, ou un `targetNamespace` de correspondance, la **suppression** ne fonctionnera pas dans cette situation en raison d’une association automatique. Dans ce cas, il est recommandé de marquer le schéma comme **n’utilisez pas les schémas sélectionnés** dans la colonne **use** .

## <a name="see-also"></a>Voir aussi
 [Éditeur XML](../xml-tools/xml-editor.md) de [la boîte de dialogue schémas XML](../xml-tools/xml-schemas-dialog-box.md) [du cache de schéma](../xml-tools/schema-cache.md)

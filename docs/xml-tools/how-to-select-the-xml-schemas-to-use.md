---
title: 'Procédure : sélectionner les schémas XML à utiliser'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06f9de6927d616d6cf08995c076246c8a45ec014
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815966"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : sélectionner les schémas XML à utiliser

L’éditeur XML fournit un cache de schéma situé dans le répertoire *%VSInstallDir%\xml\Schemas* . Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.

Utilisez la propriété **schéma** de document pour sélectionner un ou plusieurs schémas en langage XSD (XML Schema Definition). Vous pouvez sélectionner des schémas à partir du cache de schéma ou d’un autre emplacement.

Les schémas que vous spécifiez sont enregistrés dans un fichier d’options utilisateur de solution (masqué) (.* suo*), ainsi que toutes les autres propriétés de document XML. Par conséquent, vous n’êtes pas obligé de réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

> [!NOTE]
> L’éditeur peut valider à l’aide d’un schéma inline ou d’un schéma référencé par l' `xsd:schemaLocation` attribut. Pour plus d’informations, consultez [validation de document XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML à partir du cache de schéma

1. Ouvrez un fichier dans l'éditeur XML.

2. Dans la fenêtre Propriétés du document, cliquez dans le champ **schémas** . Quand le bouton Parcourir (...) apparaît, cliquez dessus.

   ![Propriété Schemas pour un fichier XML](media/properties-schemas.png)

   La [boîte de dialogue schémas XML](xml-schemas-dialog-box.md) s’ouvre. La boîte de dialogue répertorie tous les schémas avec un. extension *xsd* dans le cache de schéma (y compris les schémas référencés dans le fichier *catalog.xml* ), ainsi que tous les schémas de la solution actuelle, ouverts dans Visual Studio, référencés dans un `xsd:schemaLocation` attribut ou référencés dans la propriété **schemas** .

3. Sélectionnez les schémas à utiliser pour la validation en effectuant l'une des opérations suivantes :

   - Sélectionnez un schéma listé dans la boîte de dialogue **schémas XML** , cliquez sur la colonne **utiliser** , puis sélectionnez **utiliser ce schéma**.

     -ou-

   - Sélectionnez plusieurs schémas listés dans la boîte de dialogue **schémas XML** , cliquez avec le bouton droit et sélectionnez **utiliser ce schéma**.

4. Choisissez **OK**.

   La liste des schémas sélectionnés est recopiée dans la propriété de document **schemas** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Pour ajouter un schéma XML au cache de schéma

1. Dans la fenêtre Propriétés du document, cliquez sur le bouton dans le champ **schémas** .

2. Cliquez sur **Ajouter**.

   La boîte de dialogue **ouvrir le schéma XSD** s’ouvre.

3. Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.

4. Cliquez sur **Ouvrir**.

   Les schémas sont ajoutés au cache de schéma et la valeur de colonne **use** est définie pour **utiliser ce schéma**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Pour supprimer un schéma XML du cache de schéma

1. Dans la fenêtre Propriétés du document, cliquez sur le bouton dans le champ **schémas** .

2. Sélectionnez le schéma à supprimer, puis cliquez sur **supprimer**.

   Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.

   > [!NOTE]
   > Si vous disposez toujours d’une référence au schéma via un `schemaLocation` attribut, ou si une correspondance `targetNamespace` est **supprimée** , la suppression ne fonctionnera pas dans cette situation en raison d’une association automatique. Dans ce cas, il est recommandé de marquer le schéma comme **n’utilisez pas les schémas sélectionnés** dans la colonne **use** .

## <a name="see-also"></a>Voir aussi

- [Cache de schéma](../xml-tools/schema-cache.md)
- [Schémas XML, boîte de dialogue](../xml-tools/xml-schemas-dialog-box.md)
- [Éditeur XML](../xml-tools/xml-editor.md)

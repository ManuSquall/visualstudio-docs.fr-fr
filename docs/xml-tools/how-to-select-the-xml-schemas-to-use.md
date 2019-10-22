---
title: 'Procédure : sélectionner les schémas XML à utiliser'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601909"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : sélectionner les schémas XML à utiliser

L’éditeur XML fournit un cache de schéma situé dans le répertoire *%VSInstallDir%\xml\Schemas* . Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.

Utilisez la propriété **schéma** de document pour sélectionner un ou plusieurs schémas en langage XSD (XML Schema Definition). Vous pouvez sélectionner des schémas à partir du cache de schéma ou d’un autre emplacement.

Les schémas que vous spécifiez sont enregistrés dans un fichier d’options utilisateur de solution (masqué) (. *suo*), ainsi que toutes les autres propriétés de document XML. Par conséquent, vous n’êtes pas obligé de réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

> [!NOTE]
> L’éditeur peut valider à l’aide d’un schéma inline ou d’un schéma référencé par l’attribut `xsd:schemaLocation`. Pour plus d’informations, consultez [validation de document XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML à partir du cache de schéma

1. Ouvrez un fichier dans l'éditeur XML.

2. Dans la fenêtre Propriétés du document, cliquez dans le champ **schémas** . Quand le bouton Parcourir (...) apparaît, cliquez dessus.

   ![Propriété Schemas pour un fichier XML](media/properties-schemas.png)

   La [boîte de dialogue schémas XML](xml-schemas-dialog-box.md) s’ouvre. La boîte de dialogue répertorie tous les schémas avec un. extension *xsd* dans le cache de schéma (y compris les schémas référencés dans le fichier *Catalog. xml* ), ainsi que tous les schémas qui se trouvent dans la solution actuelle, s’ouvrent dans Visual Studio, référencés dans un attribut `xsd:schemaLocation` ou référencés dans les **schémas** propriété.

3. Sélectionnez les schémas à utiliser pour la validation en effectuant l'une des opérations suivantes :

   - Sélectionnez un schéma listé dans la boîte de dialogue **schémas XML** , cliquez sur la colonne **utiliser** , puis sélectionnez **utiliser ce schéma**.

     ou

   - Sélectionnez plusieurs schémas listés dans la boîte de dialogue **schémas XML** , cliquez avec le bouton droit et sélectionnez **utiliser ce schéma**.

4. Cliquez sur **OK**.

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
   > Si vous avez toujours une référence au schéma via un attribut `schemaLocation`, ou un `targetNamespace` de correspondance, la **suppression** ne fonctionnera pas dans cette situation en raison d’une association automatique. Dans ce cas, il est recommandé de marquer le schéma comme **n’utilisez pas les schémas sélectionnés** dans la colonne **use** .

## <a name="see-also"></a>Voir aussi

- [Cache de schéma](../xml-tools/schema-cache.md)
- [Schémas XML, boîte de dialogue](../xml-tools/xml-schemas-dialog-box.md)
- [Éditeur XML](../xml-tools/xml-editor.md)
---
title: 'Procédure : Sélectionner les schémas XML à utiliser'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526670"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : Sélectionner les schémas XML à utiliser

L’éditeur XML fournit un cache de schéma dans le *%VSInstallDir%\xml\Schemas* directory. Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.

Utilisez le **schémas** propriété pour sélectionner un ou plusieurs schémas de langage (XSD XML) de définition de schéma XML de document. Vous pouvez sélectionner les schémas à partir du cache de schéma ou un autre emplacement.

Les schémas spécifiés sont enregistrés dans un fichier d’options de solution (masqué) utilisateur (. *suo*), ainsi que tous les autres XML les propriétés de document. Par conséquent, vous n’êtes pas obligé de réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

> [!NOTE]
> L’éditeur peut valider à l’aide d’un schéma inline ou un schéma référencé par le `xsd:schemaLocation` attribut. Pour plus d’informations, consultez [validation de documents XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML à partir du cache de schéma

1. Ouvrez un fichier dans l'éditeur XML.

2. Dans la fenêtre de propriétés de document, cliquez dans le **schémas** champ. Lorsque le bouton Parcourir (...) s’affiche, cliquez dessus.

   ![Propriété des schémas pour un fichier XML](media/properties-schemas.png)

   Le [boîte de dialogue schémas XML](xml-schemas-dialog-box.md) s’ouvre. La boîte de dialogue répertorie tous les schémas avec un. *xsd* extension dans le cache de schéma (y compris les schémas référencés dans le *catalog.xml* fichier) et également n’importe quel schéma qui est référencé dans la solution actuelle, ouverte dans Visual Studio, dans un `xsd:schemaLocation` attribut ou référencés dans les **schémas** propriété.

3. Sélectionnez les schémas à utiliser pour la validation en effectuant l'une des opérations suivantes :

   - Sélectionnez un schéma dans le **schémas XML** boîte de dialogue, cliquez sur le **utilisation** colonne, puis sélectionnez **utiliser ce schéma**.

     ou

   - Sélectionnez plusieurs schémas dans le **schémas XML** boîte de dialogue, puis avec le bouton droit et sélectionnez **utiliser ce schéma**.

4. Cliquez sur **OK**.

   La liste des schémas sélectionnés est recopiée dans la **schémas** propriété de document.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Pour ajouter un schéma XML au cache de schéma

1. Dans la fenêtre de propriétés de document, cliquez sur le bouton sur le **schémas** champ.

2. Cliquez sur **Ajouter**.

   Le **ouvrir le schéma XSD** boîte de dialogue s’ouvre.

3. Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.

4. Cliquez sur **Ouvrir**.

   Les schémas sont ajoutés au cache de schéma et le **utilisation** colonne a la valeur **utiliser ce schéma**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Pour supprimer un schéma XML à partir du cache de schéma

1. Dans la fenêtre de propriétés de document, cliquez sur le bouton sur le **schémas** champ.

2. Sélectionnez le schéma à supprimer, puis cliquez sur **supprimer**.

   Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.

   > [!NOTE]
   > Si vous avez toujours une référence au schéma via un `schemaLocation` un attribut ou une mise en correspondance `targetNamespace` puis **supprimer** ne fonctionnera pas dans ce cas en raison de l’association automatique. Dans ce cas il est recommandé de marquer le schéma en tant que **n’utilisez pas les schémas sélectionnés** dans le **utiliser** colonne.

## <a name="see-also"></a>Voir aussi

- [Cache de schéma](../xml-tools/schema-cache.md)
- [Boîte de dialogue schémas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Éditeur XML](../xml-tools/xml-editor.md)
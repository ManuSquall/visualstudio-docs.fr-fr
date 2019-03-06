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
ms.openlocfilehash: 553fbc9bc8a96377a31864e1250987713714e147
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920559"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : Sélectionner les schémas XML à utiliser

L’éditeur XML fournit un cache de schéma dans le *%InstallDir%\Xml\Schemas* directory. Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.

Le **schémas** propriété de document est utilisée pour sélectionner un ou plusieurs XML schema definition language (XSD) à utiliser. Elle permet de choisir des schémas dans le cache de schéma ou de spécifier un schéma situé ailleurs dans le cache.

Les schémas spécifiés sont enregistrés dans le fichier d’options utilisateur Solution masqué (. *suo*), ainsi que tous les autres XML les propriétés de document. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

> [!NOTE]
> L'éditeur peut effectuer la validation à l'aide d'un schéma inline ou d'un schéma dont la référence est fournie par l'attribut `xsd:schemaLocation`. Pour plus d’informations, consultez [validation de documents XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML à partir du cache de schéma

1. Ouvrez un fichier dans l'éditeur XML.

2. Dans la fenêtre de propriétés de document, cliquez sur le bouton sur le **schémas** champ.

    Le **schémas XML** boîte de dialogue s’affiche. La boîte de dialogue répertorie tous les schémas avec un. *xsd* extension dans le cache de schéma (y compris les schémas référencés dans le *catalog.xml* fichier) et également n’importe quel schéma qui est référencé dans la solution actuelle, ouverte dans Visual Studio, dans un `xsd:schemaLocation` attribut ou référencés dans les **schémas** propriété.

3. Sélectionnez les schémas à utiliser pour la validation en effectuant l’une des opérations suivantes :

   - Sélectionnez un schéma dans le **schémas XML** boîte de dialogue, cliquez sur le **utilisation** colonne, puis sélectionnez **utiliser ce schéma**.

     ou

   - Sélectionnez plusieurs schémas dans le **schémas XML** boîte de dialogue, avec le bouton droit et sélectionnez **utiliser ce schéma**.

4. Cliquez sur **OK**.

    La liste des schémas sélectionnés est recopiée dans la **schémas** propriété de document.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Pour ajouter un schéma XML au cache de schéma

1.  Dans la fenêtre de propriétés de document, cliquez sur le bouton sur le **schémas** champ.

2.  Cliquez sur **Ajouter**.

     Cette opération ouvre le **ouvrir le schéma XSD** boîte de dialogue.

3.  Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.

4.  Cliquez sur **Ouvrir**.

     Les schémas sont ajoutés au schéma de mettre en cache et est le **utilisation** colonne a la valeur **utiliser ce schéma**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Pour supprimer un schéma XML à partir du cache de schéma

1.  Dans la fenêtre de propriétés de document, cliquez sur le bouton sur le **schémas** champ.

2.  Sélectionnez le schéma à supprimer, puis cliquez sur **supprimer**.

     Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.

    > [!NOTE]
    > Si vous avez toujours une référence au schéma via un `schemaLocation` un attribut ou une mise en correspondance `targetNamespace` puis **supprimer** ne fonctionnera pas dans ce cas en raison de l’association automatique. Dans ce cas il est recommandé de marquer le schéma en tant que **n’utilisez pas les schémas sélectionnés** dans le **utiliser** colonne.

## <a name="see-also"></a>Voir aussi

- [Cache de schéma](../xml-tools/schema-cache.md)
- [Boîte de dialogue schémas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Éditeur XML](../xml-tools/xml-editor.md)
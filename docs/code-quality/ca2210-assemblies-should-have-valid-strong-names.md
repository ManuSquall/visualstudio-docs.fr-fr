---
title: 'CA2210 : Les assemblys doivent porter des noms forts valides'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54f7d3a0efc2f6199c030c8dd488de3b5b158240
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231724"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210 : Les assemblys doivent porter des noms forts valides

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un assembly n’est pas signé avec un nom fort, le nom fort n’a pas pu être vérifié ou le nom fort n’est pas valide sans les paramètres de registre actuels de l’ordinateur.

## <a name="rule-description"></a>Description de la règle

Cette règle récupère et vérifie le nom fort d’un assembly. Une violation se produit si l’une des conditions suivantes est vraie :

- L’assembly n’a pas de nom fort.

- L’assembly a été modifié après la signature.

- L’assembly est à signature différée.

- L’assembly n’a pas été correctement signé ou la signature a échoué.

- L’assembly exige que les paramètres du Registre passent la vérification. Par exemple, l’outil Strong Name Tool (SN. exe) a été utilisé pour ignorer la vérification de l’assembly.

Le nom fort protège les clients du chargement à leur insu d'un assembly falsifié. Les assemblys sans noms forts ne doivent pas être déployés hors de scénarios très limités. Si vous partagez ou distribuez des assemblys qui ne sont pas signés correctement, ceux-ci peuvent être falsifiés, le Common Language Runtime peut ne pas les charger ou l'utilisateur peut être amené à désactiver une vérification sur son ordinateur. Un assembly sans nom fort présente les inconvénients suivants :

- Ses origines ne peuvent pas être vérifiées.

- La common language runtime ne peut pas avertir les utilisateurs si le contenu de l’assembly a été modifié.

- Il ne peut pas être chargé dans le Global Assembly Cache.

Notez que pour charger et analyser un assembly à signature différée, vous devez désactiver la vérification de l’assembly.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

### <a name="create-a-key-file"></a>Créer un fichier de clé

Utilisez l’une des procédures suivantes :

- Utilisez l' [outil Assembly Linker (al. exe)](/dotnet/framework/tools/al-exe-assembly-linker).

- Pour la .NET Framework 2,0, utilisez l’option `/keyfile` de `/keycontainer` compilateur ou l’option [/keyfile (spécifier une clé ou une paire de clés pour signer un assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) ou [/keycontainer (spécifier un conteneur de clé pour signer un assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) dans C++).

- Pour le .NET Framework v 1.0 ou v 1.1, utilisez l' <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> attribut ou. <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Signer votre assembly avec un nom fort dans Visual Studio

1. Dans Visual Studio, ouvrez votre solution.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés.**

3. Cliquez sur l’onglet **signature** , puis activez la case à cocher **signer l’assembly** .

4. Dans **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.

   La fenêtre **créer une clé de nom fort** s’affiche.

5. Dans **nom du fichier de clé**, tapez un nom pour votre clé de nom fort.

6. Choisissez si vous souhaitez protéger la clé par un mot de passe, puis cliquez sur **OK**.

7. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **générer**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Signer votre assembly avec un nom fort en dehors de Visual Studio

Utilisez l' [outil Strong Name Tool (SN. exe)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle uniquement si l’assembly est utilisé dans un environnement où la falsification du contenu n’est pas un problème.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Guide pratique pour signer un assembly avec un nom fort](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (outil Strong Name)](/dotnet/framework/tools/sn-exe-strong-name-tool)
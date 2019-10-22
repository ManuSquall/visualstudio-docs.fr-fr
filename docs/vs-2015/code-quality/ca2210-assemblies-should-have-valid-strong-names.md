---
title: 'CA2210 : les assemblys doivent avoir des noms forts valides | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6109e0dc18f98d0b22dfb5c548bd12447b53e61d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662982"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210 : Les assemblys doivent porter des noms forts valides
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft. Design|
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
 **Pour créer un fichier de clé**

 Utilisez l’une des procédures suivantes :

- Utilisez l’outil Assembly Linker (al. exe) fourni par le kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

- Pour le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v 1.0 ou v 1.1, utilisez l’attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> ou <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>.

- Pour la [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], utilisez l’option du compilateur `/keyfile` ou `/keycontainer` option [/keyfile (spécifier une clé ou une paire de clés pour signer un assembly)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) ou [/keycontainer (spécifier un conteneur de clé pour signer un assembly)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) dans C++).

  **Pour signer votre assembly avec un nom fort dans Visual Studio**

1. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez votre solution.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés.**

3. Cliquez sur l’onglet **signature** , puis activez la case à cocher **signer l’assembly** .

4. Dans **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.

    La fenêtre **créer une clé de nom fort** s’affiche.

5. Dans **nom du fichier de clé**, tapez un nom pour votre clé de nom fort.

6. Choisissez si vous souhaitez protéger la clé par un mot de passe, puis cliquez sur **OK**.

7. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **générer**.

   **Pour signer votre assembly avec un nom fort en dehors de Visual Studio**

- Utilisez l’outil Strong Name Tool (SN. exe) fourni par le kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si l’assembly est utilisé dans un environnement où la falsification du contenu n’est pas un problème.

## <a name="see-also"></a>Voir aussi
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Comment : signer un assembly avec un nom fort](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [sn. exe (Strong Name Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)

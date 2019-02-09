---
title: 'Procédure pas à pas : Analyse du code C/C++ pour détecter les erreurs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 26635f9f6680931d02993613f96dcfcbe623af1d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919675"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : Analyse du code C/C++ pour détecter les erreurs

Cette procédure pas à pas montre comment analyser des défauts de code potentiels du code C/C++ à l’aide de l’outil d’analyse de code pour le code C/C++.

- Exécuter l’analyse du code sur le code natif.
- Analyser les avertissements d’erreur de code.
- Traiter l’avertissement comme une erreur.
- Annoter le code source pour améliorer l’analyse des erreurs de code.

## <a name="prerequisites"></a>Prérequis

- Une copie de la [exemple de démonstration](../code-quality/demo-sample.md).
- Compréhension élémentaire de C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur le code natif

1. Ouvrez la solution de démonstration dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     La solution de démonstration remplit désormais **l’Explorateur de solutions**.

2. Dans le menu **Générer**, cliquez sur **Régénérer la solution**.

     La solution se génère sans erreurs ni avertissements.

3. Dans **l’Explorateur de solutions**, sélectionnez le projet CodeDefects.

4. Dans le menu **Projet**, cliquez sur **Propriétés**.

     Le **Pages de propriétés de CodeDefects** boîte de dialogue s’affiche.

5. Cliquez sur **analyse du Code**.

6. Cliquez sur le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.

7. Régénérez le projet CodeDefects.

     Avertissements d’analyse du code sont affichés dans le **liste d’erreurs**.

### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements d’erreur de code

1. Sur le **vue** menu, cliquez sur **liste d’erreurs**.

     Selon le profil de développeur que vous avez choisi dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devrez peut-être pointer vers **Windows autres** sur le **vue** menu, puis sur **liste d’erreurs**.

2. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6230 : Cast implicite entre types sémantiquement différents : utilisation de HRESULT dans un contexte Boolean.

     L’éditeur de code affiche la ligne qui a provoqué l’avertissement dans la fonction `bool``ProcessDomain()`. Cet avertissement indique qu’une valeur HRESULT est utilisé dans une instruction 'if' où un résultat booléen est attendu.

3. Corriger cet avertissement à l’aide de la macro SUCCEEDED. Votre code doit ressembler au code suivant :

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6282 : Opérateur incorrect : assignation à la constante dans un contexte de test. == Est-il intentionnel ?

5. Corriger cet avertissement en testant l’égalité. Votre code doit ressembler au code suivant :

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Pour traiter un avertissement comme une erreur

1. Dans le fichier Bug.cpp, ajoutez le code suivant `#pragma` instruction au début du fichier à traiter l’avertissement C6001 comme une erreur :

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Régénérez le projet CodeDefects.

     Dans le **liste d’erreurs**, C6001 apparaît maintenant comme une erreur.

3. Corrigez les deux erreurs C6001 restantes dans le **liste d’erreurs** en initialisant `i` et `j` à 0.

4. Régénérez le projet CodeDefects.

     Le projet est généré sans les avertissements ou erreurs.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation.c

1. Dans l’Explorateur de solutions, sélectionnez le projet d’Annotations.

2. Dans le menu **Projet**, cliquez sur **Propriétés**.

     Le **Pages de propriétés d’Annotations** boîte de dialogue s’affiche.

3. Cliquez sur **analyse du Code**.

4. Sélectionnez le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.

5. Régénérez le projet Annotations.

6. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6011 : Déréférencement de pointeur NULL 'newNode'.

     Cet avertissement indique que l’appelant pour vérifier la valeur de retour. Dans ce cas, un appel à **AllocateNode** peut retourner une valeur NULL (consultez le fichier d’en-tête annotations.h la déclaration de fonction d’AllocateNode).

7. Ouvrez le fichier annotations.cpp.

8. Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Régénérez le projet Annotations.

     Le projet est généré sans les avertissements ou erreurs.

### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source

1. Annoter des paramètres formels et la valeur de retour de la fonction `AddTail` en utilisant les conditions de pré-script et post-script comme indiqué dans cet exemple :

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Régénérez le projet Annotations.

3. Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6011 : Déréférencement de pointeur NULL 'node'.

     Cet avertissement indique que le nœud passé dans la fonction peut être null et indique le numéro de ligne où l’avertissement a été déclenché.

4. Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Régénérez le projet Annotations.

     Le projet est généré sans les avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Analyse du Code managé pour les erreurs de Code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[analyse du Code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
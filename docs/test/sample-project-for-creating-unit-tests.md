---
title: Exemple de code pour la création de tests unitaires
description: Cet article fournit un exemple de code que vous pouvez tester avec des tests unitaires dans Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a6627b96daefa48c9a72fd84726775fc449bde
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="sample-code-for-testing"></a>Exemple de code de test

Cet exemple de code contient une classe, *BankAccount*, avec différentes méthodes que vous pouvez tester par le biais de tests unitaires.

Le code est utilisé dans les procédures suivantes :

- [Créer et exécuter des tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Cette procédure pas à pas vous guide à travers les étapes de création et de personnalisation des tests unitaires, de leur exécution et de l'examen des résultats des tests.
- [Utiliser l’utilitaire de test en ligne de commande](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). Dans cette procédure pas à pas, vous utilisez l'utilitaire en ligne de commande MSTest.exe pour exécuter les tests et afficher les résultats.

## <a name="sample-code"></a>Exemple de code

L'unique erreur intentionnelle de cet exemple est que dans la méthode Debit « m_balance += amount » doit avoir le signe moins (-) et non le signe plus (+) devant le signe égal.

```csharp
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }
    }
}
```

/* Les noms de sociétés, d'organisations, de produits, de domaines, d'adresses de messagerie, de logos, de personnes, de lieux et d'événements mentionnés dans les exemples sont fictifs. Toute ressemblance avec des noms ou des événements réels est purement fortuite et involontaire. \*/

## <a name="create-the-project"></a>Créer le projet

Pour utiliser ce code, créez d’abord un projet pour lui dans Visual Studio. Suivez les étapes pour créer le projet dans [Procédure pas à pas : créer et exécuter des tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : créer et exécuter des tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Procédure pas à pas : utiliser l’utilitaire de test en ligne de commande](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)

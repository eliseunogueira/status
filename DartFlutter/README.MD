# Dart & Flutter

# 
24-07-2022 00:03 -> 28

```dart

void main() {
  var deck = new Deck();
  //deck.shuffle();
  //print(deck.cardsWithSuit('Diamonds'));
  deck.removeCard('Diamonds', 'Ace');
  print(deck);
}

class Deck {
  List<Card> cards = [];
  Deck() {
    var ranks = [
      'Ace',
      'Two',
      'Three',
      'Four',
      'Five',
      'Six',
      'Seven',
      'Eight',
      'Nine',
      'Ten',
      'Jack',
      'Queen',
      'King'
    ];
    var suits = ['Diamonds', 'Hearts', 'Club', 'Spades'];

// for ever suits Diamons (13 cards each)
    for (var suit in suits) {
      for (var rank in ranks) {
        var card = new Card(rank: rank, suit: suit);
        cards.add(card);
      }
    }
  }
  @override
  String toString() {
    return cards.toString();
  }

  shuffle() {
    cards.shuffle();
  }

/**
 * cardsWithSuit(String suit) {
    return cards.where((card) {
      return card.suit == suit;
    });
  }
 */
  cardsWithSuit(String suit) {
    return cards.where((card) => card.suit == suit);
  }

  deal(int handSize) {
    var hand = cards.sublist(0, handSize);
    cards = cards.sublist(handSize);
    return hand;
  }
/*
  removeCard(String suit, String rank) {
    cards.removeWhere((card) {
      return (card.suit == suit) && (card.rank == rank);
    });
  }
*/

  removeCard(String suit, String rank) {
    cards.removeWhere((card) => (card.suit == suit) && (card.rank == rank));
  }
}

class Card {
  String suit;
  String rank;
  Card({required this.rank, required this.suit});

  @override
  String toString() {
    return '$rank of $suit';
  }
}
```
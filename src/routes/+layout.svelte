<script lang="ts">
  import Notification from '$lib/components/Notification.svelte';
  import Navigation from '$lib/components/Navigation.svelte';

  // Top-level site categories provided from the 'server' (decluttered from NavLinks)
  const categories = [
    { title: 'All Categories', href: '/' },
    {
      title: 'Home & Kitchen',
      panel: {
        description: 'Essentials for every room — cookware, storage, cleaning and decor.',
        columns: [
          { heading: 'Kitchen', links: [ { title: 'Cookware' }, { title: 'Small Appliances' }, { title: 'Dinnerware' } ] },
          { heading: 'Home Care', links: [ { title: 'Cleaning Supplies' }, { title: 'Storage & Organization' }, { title: 'Bedding' } ] },
          { heading: 'Decor', links: [ { title: 'Rugs' }, { title: 'Lighting' }, { title: 'Wall Art' } ] }
        ]
      }
    },
    {
      title: 'Clothing',
      panel: {
        description: 'Fashion for the whole family — casual, workwear and seasonal essentials.',
        columns: [
          { heading: "Men's", links: [ { title: 'Shirts' }, { title: 'Jeans' }, { title: 'Outerwear' } ] },
          { heading: "Women's", links: [ { title: 'Dresses' }, { title: 'Tops' }, { title: 'Activewear' } ] },
          { heading: "Kids'", links: [ { title: 'Infant' }, { title: 'Toddlers' }, { title: 'Schoolwear' } ] }
        ]
      }
    },
    {
      title: 'Electronics',
      panel: {
        description: 'Latest gadgets and everyday electronics — phones, audio, and accessories.',
        columns: [
          { heading: 'Audio', links: [ { title: 'Headphones' }, { title: 'Speakers' }, { title: 'Soundbars' } ] },
          { heading: 'Mobile', links: [ { title: 'Smartphones' }, { title: 'Cases & Chargers' }, { title: 'Wearables' } ] },
          { heading: 'Computing', links: [ { title: 'Laptops' }, { title: 'Peripherals' }, { title: 'Monitors' } ] }
        ]
      }
    },
    {
      title: 'Furniture',
      panel: {
        description: 'Comfortable and stylish furniture for living rooms, bedrooms and offices.',
        columns: [
          { heading: 'Living Room', links: [ { title: 'Sofas' }, { title: 'Coffee Tables' }, { title: 'TV Stands' } ] },
          { heading: 'Bedroom', links: [ { title: 'Beds' }, { title: 'Dressers' }, { title: 'Nightstands' } ] },
          { heading: 'Office', links: [ { title: 'Desks' }, { title: 'Chairs' }, { title: 'Storage' } ] }
        ]
      }
    },
    {
      title: 'Appliances',
      panel: {
        description: 'Big and small appliances to make everyday life easier.',
        columns: [
          { heading: 'Large', links: [ { title: 'Refrigerators' }, { title: 'Washing Machines' }, { title: 'Ovens' } ] },
          { heading: 'Small', links: [ { title: 'Blenders' }, { title: 'Coffee Makers' }, { title: 'Air Fryers' } ] }
        ]
      }
    },
    {
      title: 'Deals',
      panel: {
        description: 'Daily deals, bundles and clearance — save on top categories.',
        columns: [
          { heading: 'Top Deals', links: [ { title: 'Today’s Picks' }, { title: 'Clearance' }, { title: 'Bundle Offers' } ] },
          { heading: 'By Category', links: [ { title: 'Electronics Deals' }, { title: 'Home Deals' }, { title: 'Fashion Deals' } ] }
        ]
      }
    }
  ];
</script>

<Notification />
<Navigation items={categories} />

<slot />

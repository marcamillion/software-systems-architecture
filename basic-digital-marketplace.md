# Basic Digital Marketplace

This marketplace facilitates the sale of digital files.

### Carts
* total (float)

> has_many :line_items, as: :line_itemable <br />
> has_many :items, through: :line_items

### Item
* name (string)
* link (string)
* description (text)
* price (float)
* user_id (integer)
* is_downloadable (boolean), default: false
* downloadable_file_name (string)
* downloadable_content_type (string)
* downloadable_file_size (string)
* downloadable_updated_at (string)
* slug (string)
* is_example (string)

> has_many :line_items

### LineItem
* item_id (integer)
* line_itemable_id (integer)
* line_itemable_type (string)
* price (float), default(0.0), not null
* description (string)

> belongs_to :line_itemable <br />
> belongs_to :item

### Orders
* user_id (integer)
* total (float)

> has_many :line_items, as: :line_itemable <br />
> belongs_to :user <br />
> has_many :sales <br />
> has_many :vendors, source: :user, through: :sales, uniq: true

### Sale

* user_id (integer)
* item_id (integer)
* amount (float)
* order_id (integer)
  
> belongs_to :user <br />
> belongs_to :item <br />
> belongs_to :order <br />

### Upload

* name (string)

==========================================
Fiscal positions (tax and account mapping)
==========================================

Default taxes and accounts are set on products and customers to create new transactions on the fly.
However, depending on the customers’ and providers’ localization and business type, different taxes
and transaction accounts might be necessary.

**Fiscal positions** allow the creation of rules to adapt the taxes and accounts used for a
transaction automatically.

.. image:: fiscal_positions/fiscal-positions-intra-community.png
   :alt: Example: Belgian to Intra-Community tax mapping with Fiscal Positions in Odoo Accounting

They can be applied :ref:`automatically <fiscal_positions/automatic>`, :ref:`manually
<fiscal_positions/manual>`, or :ref:`assigned by default to a partner <fiscal_positions/partner>`.

.. note::
   Several default fiscal positions are available as part of your :ref:`fiscal localization
   package <fiscal_localizations/packages>`.

Configuration
=============

 .. _fiscal_positions/mapping:

Tax and account mapping
-----------------------

To edit or create a fiscal position, go to :menuselection:`Accounting --> Configuration --> Fiscal
Positions`, and open the entry to modify or click on :guilabel:`New`.

The mapping of taxes and accounts is based on the default taxes and accounts defined in the
product forms.

- To map to another tax or account, fill out the right column (:guilabel:`Tax to Apply`/
  :guilabel:`Account to Use Instead`).

.. image:: fiscal_positions/fiscal-position-tax-map.png
   :alt: Tax mapping for fiscal positions

.. image:: fiscal_positions/fiscal-position-account-map.png
   :alt: Account mapping for fiscal positions

- To remove a tax, leave the field :guilabel:`Tax to Apply` empty.
- To replace a tax with several other taxes, add multiple lines using the same :guilabel:`Tax on
  Product`.

.. note::
   The mapping only works with *active* taxes. Therefore, make sure they are active by going to
   :menuselection:`Accounting --> Configuration --> Taxes`.

Application
===========

.. _fiscal_positions/automatic:

Automatic application
---------------------

To automatically apply a fiscal position following a set of conditions, go to
:menuselection:`Accounting --> Configuration --> Fiscal Positions`, open the fiscal position to
modify, and tick :guilabel:`Detect Automatically`.

From there, several conditions can be activated:

- :guilabel:`VAT Required`: the customer's VAT number must be present on their contact form.
- :guilabel:`Country Group` and :guilabel:`Country`: the fiscal position is only applied to the
  selected country or country group.

.. image:: fiscal_positions/fiscal-positions-country.png
   :alt: Example of settings to apply a Fiscal Position automatically

.. note::
   Taxes on **eCommerce orders** are automatically updated once the visitor has logged in or filled
   out their billing details.

.. important::
   The fiscal positions' **sequence** defines which fiscal position is applied if all conditions
   set on multiple fiscal positions are met simultaneously.

   For example, suppose the first fiscal position in a sequence targets *country A* while the second
   fiscal position targets a *country group* that comprises *country A*. In that case, only the
   first fiscal position will be applied to customers from *country A*.

.. _fiscal_positions/manual:

Manual application
------------------

To manually select a fiscal position, open a sales order, invoice, or bill, go to the
:guilabel:`Other Info` tab and select the desired :guilabel:`Fiscal Position` before adding product
lines.

.. image:: fiscal_positions/fiscal-positions-transactions.png
   :alt: Selection of a Fiscal Position on a Sales Order / Invoice / Bill in Odoo Accounting

.. _fiscal_positions/partner:

Assign to a partner
-------------------

To define which fiscal position must be used by default for a specific partner, go to
:menuselection:`Accounting --> Customers --> Customers`, select the customer, open the
:guilabel:`Sales & Purchase` tab, and select the :guilabel:`Fiscal Position`.

.. image:: fiscal_positions/fiscal-position-customer.png
   :alt: Selection of a Fiscal Position for partner

.. seealso::
   - :doc:`taxes`
   - :doc:`taxcloud`
   - :doc:`B2B_B2C`

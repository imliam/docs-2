---
title: The <code>mount()</code> method
extends: _layouts.documentation
section: content
---

## Initial Parameters {#initial-params}

You can pass data into a component by passing additional parameters into the `@livewire` directive. For example, let's say we have a `ShowContact` Livewire component that needs to know which contact to show. Here's how you would pass in the contact id.

@code(['lang' => 'php'])
@verbatim
@livewire('show-contact', $contactId)
@endverbatim
@endcode

@code(['lang' => 'php'])
@verbatim
use Livewire\Component;

class ShowContact extends Component
{
    public $name;
    public $email;

    public function mount($id)
    {
        $contact = User::find($id);

        $this->name = $contact->name;
        $this->email = $contact->email;
    }

    ...
}
@endverbatim
@endcode

You can pass multiple parameters to the `mount()` hook and receive them like so:

@code(['lang' => 'php'])
@verbatim
@livewire('show-contact', $contactId, $profilePhotoUrl)
@endverbatim
@endcode

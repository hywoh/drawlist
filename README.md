# drawlist
A draw-list system for rendering to Unreal Engine's Canvas.

# Example Usage
```c++
Canvas::NewFrame(canvas); // Create a new frame passing in your canvas

Canvas::DrawList drawList; // Create a drawlist that you manage. You can clear this at anytime with DrawList::Clear();
drawList->AddText(L"Hello", { 500, 500 }, true, FLinearColor(1.0f, 1.0f, 1.0f, 1.0f), Canvas::TextEffect::OUTLINE, Canvas::TextFont::POPPINS_MEDIUM); // Add text to the drawlist

Canvas::GetPersistentDrawlist()->AddLine({ 0, 0 }, { 1920, 1080 }, 5, FLinearColor(1.0f, 1.0f, 1.0f, 1.0f)); // Render a white 5 pixel thick line from top-left to bottom-right to the persistent draw list.


Canvas::RenderDrawList(drawList); // Render the given drawlist.
Canvas::RenderDrawList(Canvas::GetPersistentDrawlist()); // Render the persistent drawlist
Canvas::EndFrame();
```


